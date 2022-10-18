---
published: true
---
---
## Summary
This week I followed a number off different implementations of Word2Vec. I followed Vatsal's example impementation using Shakespeare text as a data source. I also examined the Word2Vec model in gensim and got familiar with how its implemented in Code, and the similarity operations the model can perform, such as finding the most similar word to a given word, or finding a word in a list that doesnt match based on context.

---

## Word2Vec example implementation
The shakespeare text used is avaiable at [Vatsal's GitHub](https://github.com/vatsal220/medium_articles/blob/main/w2v/data/shakespeare.txt)

The file is structured as follows:

"ACT I"

"SCENE I. London. The palace."

"Enter KING HENRY, LORD JOHN OF LANCASTER, the EARL of WESTMORELAND, SIR WALTER BLUNT, and others"

... And so on.

The code itself guided me through the process of preprocessing the shakespeare data, removing stopwords from the text and initialising a gensim word2vec model using the filtered lines from the shakespeare data. The word2Vec model was then queried for the words most similar to "Thou". The following was the output of the Word2Vec model (w):
![Word2vec output](https://i.imgur.com/jzSeGEB.png)

The highest word in terms of similarity to 'thou' is 'thyself', which makes perfect sense.


## Gensim Word2Vec model
The most likely implementation of Word2Vec I will use is the model available through gensim. I spent a great deal of time reading the [documentation](https://radimrehurek.com/gensim/models/word2vec.html) available on the Word2Vec model in gensim, mainly learning what the various parameters are and how the affect the training and output of the model.

Following that, I downloaded some pretrained models through gensim (example: 'word2vec-google-news-300') and tested out some of the similarity operations available through the KeyedVector downloaded.

---
## Plans for week 06
Week 06 will be busy, with a presentation based on this FYP project along with a number of other things. However, I would like to get started researching some of the ML models I could use in conjunction with my word embeddings from Word2Vec. In particular, I am curious about LSTM. which is a variation of a Recurrent Neural Network.
