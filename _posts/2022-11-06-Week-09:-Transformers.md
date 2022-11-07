---
published: true
layout: post
---
---
## Summary

During weeks 7 and 8, I was primarily focusing on learning tensorflow keras and going through some of the Google ML courses. This killed two birds with one stone as I was working on assignments for one of my other modules this semester, Neural Computing. An assignment on CNNs taught me about Transfer Learning, the practice of using a pretrained model and repurposing it for a new task. This gave me ideas for the implementation of my Next Word Predictor, more on that later.

I resumed research again at the start of this week and had planned to continue loking into LSTM and some implementations. However, I quickly came across something more interesting: a more recent technological advancement in the field of NLP that is Transformers. I quickly learned the advantages that transformers offer over older LSTM and RNN based models, namely computational efficiency, faster training times, less parameters overall, and the ability for transfer learning.

I also experimented with some code to try out transformers. I used a subset (~1/8) of the GenericsKB dataset (Collection of ~3.4M sentences that contain some generic truth about the world like "Small businesses can receive a state tax credit for offering employee wellness programs."). I trained a simple transformer model on 127000 sentences from the dataset. The model itself made use of 5 transformer decoder layers. After training for 5 epochs, the model's test loss was 2.5443, perplexity was 12.7339, and accuracy was 0.4683. Meaning I still have many optimisations to make, especially in relation to the dataset itself.

---
## What are Transformers?
I initially learned about Transformers while researching LSTM. i came across the video ["LSTM is dead. Long Live Transformers!"](https://www.youtube.com/watch?v=S27pHKBEp30) where Leo Dirac gives a presentation on the progression from simple Bag of Words models to RNNs to LSTM and now Transformers. He makes reference to the orginal paper describing Transformers: ["Attention Is All You Need"](https://arxiv.org/pdf/1706.03762.pdf) by Vaswani et al. The paper is primarily concerned with the task of machine translation, meaning there is an encoder-decoder architecture involved.

![](https://i.imgur.com/4lWevrl.png)
_The Transformer model architecture, by the authors of "Attention Is All You need"_

The encoder block is on the left, while the decoder block is on the right. Looking at just the encoder block, the key elements are the Positional Embedding, Multi-head attention, and a fully connected layer. The attention mechanism is the key to allowing the transformer model to operate on documents of variable length.

---
### Attention
The attention function is described by Vaswani et al. as **"mapping a query and a set of key-value pairs to an output, where the query, keys, values, and output are all vectors. The output is computed as a weighted sum of the values, where the weight assigned to each value is computed by a compatibility function of the
query with the corresponding key."** 

![](https://i.imgur.com/YzsjanM.png)
_Diagrams from "Attention Is All You Need" comparing scaled dot product and multihead attention_

In scaled Dot Product Attention, for every output position, a query is generated, and for every input that is being considered, a key is generated. We take the dot product of the query and the key to get something called the **"relevance score"**. The relevance score is calculated for every key and each value is normalised. After that, softmax is applied to obtain the weights of all the values.

Multi headed attention then is simply doing that process 8 times in parallel with different Q,K,V matrices. This allows the network to learn 8 different semantic meanings of attention. In the context of machine translation, this could allow for one attention head to be dedicated to grammar, one for vocabulary, etc.

---

### Positional Encoding
Without positional encoding, attention would simply amount to a bag of words. It would have difficulty differentiating between "live to work" and "work to live". The transformer model takes some inputs and uses Word2Vec to calculate a vector for each input token. Then sines and cosines of different frequencies are added on top of the generated embeddings, allowing the model to reason about the relative positioning of tokens. This is how the model is capable of understanding position. 

---

### Transformers Vs. LSTM
- Transformers avoid the usage of sigmoid and tanh activation functions -> (avoid vanishing / exploding gradient problem).
- Transformers make more use of ReLU as an activation function -> faster computation, insensitive to random initialisation.
- Transformers can utilise GPU better by working in parallel on tasks such as the attention function. Older models like LSTM require work to be done sequentially.
- Transformers also have less overall parameters than LSTM models.
- As such, Transformers train faster than LSTM or RNN based models
- LSTM models are not capable of transfer learning. Transformers are.
- LSTM models are better when sequence lengths are long or approaching infinite. transformers are O(N^2)
- LSTM outperforms Transformers for small / fixed dataset sizes

---

## Conclusion
Having researched more about Transformers and understanding their advantages over LSTM, I am more inclined to utilise transformers over LSTM based models. The ability to use transfer learning means I can potentially reuse a model such as GPT-2, etc to enhance the accuracy of my predictor without needing nearly as much data.

---

## Plans for Week 10
I will continue experimenting with code implementations of Transformers and finding an ideal dataset for the task. I will also investigate transfer learning using pretrained transformer models.