## Introduction

Question answering (QA) is one of the most widely researched topics in Natural
Language Processing. The objective in contextual QA is to locate the answer to
a question within a given context. Previously, the state-of-the-art benchmark for
QA models was its performance on the SQuAD 1.0[1] data set, where the answer
was guaranteed to be located within the context. Recently, with the release of
SQuAD 2.0, the answer is no longer guaranteed to be within the context. To tackle the QA problem, we test two architectures BIDAF and QAnet. I carried out the project during the course CS224N with two classmates Guillermo Bescos and Lucas Soffer. 

## Approaches

# BIDAF

For BiDAF, we started from a code provided in the course CS224N by Mina Lee and improve it by doing modifications such as adding char embeddings generated from CNN. 
BiDAF can be decomposed into five parts : embedding, encoder, attention, modeling
and output layers. The encoder step is computed from bidirectionnal LSTM and the attention gathers similarity between context and queries encoded vectors.Then the Modeling and Output layer prepares vectors in enables to computes the probability that the context sentence starts and finish at two specific index.

#QAnet

For QAnet, we implemented from scratch the architecture from "Qanet: combining local convolution with global self-attention for reading"[3]. As BiDaf, QAnet can be decomposed into five parts : embedding, encoder, context-query attention, modeling
and output layers. Contrary to BiDAF, the embedding and model encoder are composed of a stack
of encoder blocks each consisting of a fixed number of depth-wise separable convolutions followed
by a single multihead self-attention layer and a single feed-forward layer. The intuition behind this architecture is that the convolutional layers should capture local structure and the attention mechanism should capture long-distance contextual interactions.

## Setup

1. Make sure you have [Miniconda](https://conda.io/docs/user-guide/install/index.html#regular-installation) installed

2. cd into src, run `conda env create -f environment.yml`

3. Run `source activate squad`
  
4. Run `python setup.py`
    1. This downloads SQuAD 2.0 training and dev sets, as well as the GloVe 300-dimensional word vectors (840B)
    2. This also pre-processes the dataset for efficient data loading 

5. Browse the code in `train.py`
   

## References

References
[1] Pranav Rajpurkar, Jian Zhang, Konstantin Lopyrev, and Percy Liang. Squad: 100, 000+ questions
for machine comprehension of text. CoRR, abs/1606.05250, 2016.
[2] Pranav Rajpurkar, Robin Jia, and Percy Liang. Know what you don’t know: Unanswerable
questions for squad. CoRR, abs/1806.03822, 2018.
[3] Minh-Thang Luong† Rui Zhao Kai Chen Mohammad Norouzi Quoc V. Le Adams Wei Yu1,
David Dohan†. Qanet: combining local convolution with global self-attention for reading
comprehension. In International Conference on Learning Representations (ICLR), 2018.
[4] Ali Farhadi Minjoon Seo, Aniruddha Kembhavi and Hannaneh Hajishirzi. Bidirectional attention
flow for machine comprehension. In International Conference on Learning Representations
(ICLR), 2017.
[5] Mina Lee. Starter code for stanford cs224n default final project on squad 2.0. https://github.
com/minggg/squad, 2020.

