---
published: true
layout: post
---
---
## Summary

I spent this week researching some of the technologies that could be used as the core for my Next Word Predictor project. My FYP advisor gave one suggestion that was a combination of Word2Vec and a neural network, so I began by reading up on Word2Vec and how it works.

## What Is Word2Vec?

Word2Vec is a tool for generating word embeddings, which are a popular approach to many problems in Natural Language Processing. The overall output of Word2Vec is embeddings associated to each unique word passed through the algorithm.

[Source: "Word2Vec Explained" by Vatsal of Towards Data Science](https://towardsdatascience.com/word2vec-explained-49c52b4ccb71)

## What Are Word Embeddings?

Word Embeddings depict how humans understand language to a machine, so that the machine can process and analyse the given text. Individual words are transformed into a numerical representation (a vector) of the word. Each word is mapped to one vector, then this vector is learned in a fashion that resembles a neural network. The vectors capture various characteristics of their respective word with regard to the given text that word appears in. The vectors can be used in multiple scenarios, such as identifying the similarity or dissimilarity between words.

## The Architecture of Word2Vec

Word2Vec's effectiveness comes from its ability to group together various vectors of similar words. With a large dataset, Word2Vec can make strong estimates about a word's meaning based on their occurrences in the text. These estimates yield word associations with other words in the text.

Word2Vec is comprised of two main architectures, that is two main methods for generating word embeddings: the Continuous Bag of Words model (CBOW) and the Continuous Skip Gram Model. To learn more about these I read this paper titled ["Efficient Estimation of Word Representations in Vector Space"](https://arxiv.org/pdf/1301.3781.pdf). The objective of the paper was to examine the efficiency of various models and the differences in quality of vector representations of words between them, CBOW and Skip-gram included. In the authors' testing of the various models, CBOW and Skip-gram both attained remarkable results in terms of accuracy, and significant achievements in terms of efficiency.

### CBOW

The CBOW model architecture behaves like a feed forward neural network. It attempts to predict a target word when given a number of context words that surround it. An example given in Vatsal's article is if "a" is the missing target word in the sentence "Have a great day", the remaining context words ["have", "great", "day"] will have their vector representations fed to the CBOW model, which will then try to predict the missing target word. 

![Architecture of CBOW model](https://i.imgur.com/ISgpgaG.png)

### Skip-gram

The Skip-gram model behaves in an almost opposite fashion to the CBOW model. It is a simple neural network with one hidden layer trained in order to predict the probability of a given word being present when an input word is present. It takes a target word as input and tries to predict what context words come before and after the target word.

![Architecture of Skip-gram model](https://i.imgur.com/YQBezCJ.png)

## Which Model Would Be Better?

Given that I will be building a Next word Predictor, I believe that the CBOW model is the right choice. The input would be a partially completed sentence (or no sentence at all), meaning there would already be a number of context words available before the target word I would like to predict. That means I'd only need to generate the word vectors for the context words and feed them in to predict the most probable next word in the sentence. 

---

## What is my objective for Week 05?

One of my main objectives for next week is to follow the example implementation of Word2Vec in Vatsal's article so I can attain a better understanding of how Word2Vec is utilised and what the code would look like in the implementation.

I would also like to get a clearer picture of Word2Vec overall, and maybe even research some alternate solutions/implementations for the Next Word Predictor problem.

That's all for now. Thanks for reading!
