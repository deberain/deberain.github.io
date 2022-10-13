---
published: false
---
---
## Summary
This week I followed Vatsal's tutorial for an example Word2Vec implementation using Shakespeare text as input.


## Word2Vec example implementation
The shakespeare text used is avaiable at [Vatsal's GitHub](https://github.com/vatsal220/medium_articles/blob/main/w2v/data/shakespeare.txt)

The file is structured as follows:

"ACT I"

"SCENE I. London. The palace."

"Enter KING HENRY, LORD JOHN OF LANCASTER, the EARL of WESTMORELAND, SIR WALTER BLUNT, and others"

... And so on.

The code itself guided me through the process of preprocessing the shakespeare data, removing stopwords from the text and initialising a gensim word2vec model using the filtered lines from the shakespeare data. The word2Vec model was then queried for the words most similar to "Thou". The following was the output of the Word2Vec model (w is my Word2Vec model):
![Word2vec output](https://i.imgur.com/jzSeGEB.png)

The highest word in terms of similarity to 'thou' is 'thyself', which makes perfect sense. 




