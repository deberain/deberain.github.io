---
published: false
layout: post
---
---
## Summary

During weeks 7 and 8, I was primarily focusing on learning tensorflow keras and going through some of the Google ML courses. This killed two birds with one stone as I was working on assignments for one of my other modules this semester, Neural Computing. An assignment on CNNs taught me about Transfer Learning, the practice of using a pretrained model and repurposing it for a new task. This gave me ideas for the implementation of my Next Word Predictor, more on that later.

I resumed research again at the start of this week and had planned to continue loking into LSTM and some implementations. However, I quickly came across something more interesting: a more recent technological advancement in the field of NLP that is Transformers. I quickly learned the advantages that transformers offer over older LSTM and RNN based models, namely faster training times, less parameters overall, and the ability for transfer learning.

---
### What are Transformers?
I initially learned about Transformers while researching LSTM. i came across the video ["LSTM is dead. Long Live Transformers!"](https://www.youtube.com/watch?v=S27pHKBEp30) where Leo Dirac gives a presentation on the progression from simple Bag of Words models to RNNs to LSTM and now Transformers. He makes reference to the orginal paper describing Transformers: ["Attention Is All You Need"](https://arxiv.org/pdf/1706.03762.pdf) by Vaswani et al. The paper is primarily concerned with the task of machine translation, meaning there is an encoder-decoder architecture involved.

![](https://i.imgur.com/4lWevrl.png)