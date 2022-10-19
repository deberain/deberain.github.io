---
published: true
layout: post
---
---
## Summary
This week I started researching potential implementations for the ML model of the next word predictor. I focused on Recurrent Neural Networks, in particular Long Short Term Memory (LSTM). RNN based models are perfect as they have the ability to remember previous input, making them ideal for problems with sequential data, such as the characters in a word that the model is attempting to predict.

RNNs have the issue of forgetting their previous inputs after a period of time due to vanishing gradients and explosive gradients. LSTM and GRU (Gated Recurrent Units) are often used as solutions to this flaw in RNNs.

---
### Recurrent Neural Networks
Recurrent Neural networks exist to deal with the task of sequential data. Consider a standard Feedforward neural network. The information flows in one direction from the input nodes to the output nodes. Feedforward networks have no mechanism to 'memorise' previous inputs and refer to them during evaluation, and as such arent equipped to deal with problems concerning sequential data, such as text prediction, language translation, etc. 

There are different types of RNN models, such as vector-to-sequence, sequence-to-sequence models, and so on. For the purpose of the next word predictor, I will use a sequence-to-sequence model, as our input is a sequence of words and, likewise, our output is a sequence of words that the model has predicted.

RNNs have information that flows both ways. Inputs proceed forward as normal, just like a conventional Feedforward neural network. The difference is that the RNN will loop information about the input and send it back to be used in conjunction with the next input. This pattern continues until typically a vanishing or explosive gradient is encountered. This is one of the fundamental flaws of RNNs: they can memorise data, but they can't hold onto it for too long. Solutions to this issue are the use of LSTM or GRU.

### Long Short Term Memory
LSTM models were created with the intent to mitigate the vanishing and exploding gradient problem. Every hidden unit in the traditional RNN is replaced with an 'LSTM Cell' and an additional connection is made between cells that transfers cell state. Each unit has three gates inside it.

- **The Input gate**, which controls whether the memory cell is updated.
- **The Forget gate**, which controls whether the memory cell gets reset to 0.
- **The Output gate**, which controls whether the information of the current cell state is made visible. 

The gates all have a sigmoid activation. In addition to the gates, there is another vector that modifies the cell state. it has the tanh activation so that the cell state can flow longer without vanishing or exploding.

The result is a model that can memorise far longer sequences than a traditional RNN could hope to achieve.

---
## Plans for Week 07
Having learned more about LSTM, I want to experiment with implementing it using code (likely tensorflow keras) and potentially training it on some sample data. There may be some value in also researching GRU models.

---
## Sources
["How Recurrent Neural Networks work" by Simeon Kostadinov of towardsdatascience.com](https://towardsdatascience.com/learn-how-recurrent-neural-networks-work-84e975feaaf7)

["Text Prediction Using Machine Learning" by Khalid, M.](https://www.diva-portal.org/smash/get/diva2:1632760/FULLTEXT02)

["LSTM Networks - Explained" by YouTube channel CodeEmporium](https://www.youtube.com/watch?v=QciIcRxJvsM)
