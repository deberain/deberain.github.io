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
_The Transformer model architecture, by the authors of "Attention Is All You need"_

The encoder block is on the left, while the decoder block is on the right. Looking at just the encoder block, the key elements are the Positional Embedding, Multi-head attention, and a fully connected layer. The attention mechanism is the key to allowing the transformer model to operate on documents of variable length. 

### Attention
The attention function is described by Vaswani et al. as **"mapping a query and a set of key-value pairs to an output, where the query, keys, values, and output are all vectors. The output is computed as a weighted sum of the values, where the weight assigned to each value is computed by a compatibility function of the
query with the corresponding key."** 

![](https://i.imgur.com/YzsjanM.png)
_Diagrams from "Attention Is All You Need" comparing scaled dot product and multihead attention_

In scaled Dot Product Attention, for every output position, a query is generated, and for every input that is being considered, a key is generated. We take the dot product of the query and the key to get something called the **"relevance score"**. The relevance score is calculated for every key and each value is normalised. After that, softmax is applied to obtain the weights of all the values.

Multi headed attention then is simply doing that process 8 times in parallel with different Q,K,V matrices. This allows the network to learn 8 different semantic meanings of attention. In the context of machine translation, this could allow for one attention head to be dedicated to grammar, one for vocabulary, etc.

### Positional Encoding