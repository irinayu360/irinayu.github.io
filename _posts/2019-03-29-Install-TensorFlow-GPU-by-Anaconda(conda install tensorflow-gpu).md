---
layout:     post
title:      Word2Vec SkipGram with Math and Implementation
subtitle:   A in-depth explanation of Word2vec via Skipgram of both mathematical theory and practical implementation
date:       2022-03-03
author:     Xinli (Irina) Yu
header-img: img/horse.jpeg
catalog: true
tags:
    - Machine Learning
    - NLP
    - Word2vec
    - Python
---


Word2vec is a technique for natural language processing to learn word embeddings using neural network.

---

## What is the purpose of word2vec?
The purpose and usefulness of word2vec is to group the vectors of similar words together in vector space. That is, it detects similarities mathematically.

Word2vec creates embedding vectors that are distributed numerical representations of word features such as the context of individual words. The idea is a word could be intuitively represented by its context. As an old saying once said, a man is known by the company he/she keeps, same goes the word.

The big advantage of word2vec over TF-IDF is it retains the semantic meaning of different words in a document. The context information is not lost.

## How the word embeddings are learnt?

The word2vec is trained by first designing a model for another task, in which the parameters are word embedding. As we improve the accuracy for the particular task by iterations and back propagation, the parameters, i.e., word embedding is also becoming more and more accurate.
The particular task and model we use for word2vec is the SkipGram model. We are not interested in the prediction of the model, but the by-product(word vectors/embeddings) of the model.

## SkipGram model

We could use a SkipGram model to train these word embeddings. Given the center word “jumped”, the model will be able to predict or generate the surrounding words “The”, “cat”, “over”, “the”, “puddle”. Here we call the word “jumped” the context. We call this type of model a SkipGram model.

## Training with normal SoftMax

The loss is cross entropy loss. Suppose we would like to learn a N-dim word embedding, the vocabulary size is |V|-dim, and we use a window size of m.
Input would be a |V|-dim one-hot vector representing the center word, for example “brown”. The model is trying to predict the context words around the center word, for example “fox”, “jump” etc.
Let us take the pair (“brown”, “fox”) as an example to illustrate the training process.

Step 1:
The input |V|-dim one-hot is first mapped into a N-dim vector v via embedding lookup matrix U of size (|V|, N), which is the hidden layer shown in the figure.

Step 2:
The hidden layer vector v is mapped by another context embedding matrix V of size (N, |V|) to a |V|-dim vector. The element represents the likelihood of each word in vocabulary occurring with the center word.

Step 3:
Then a SoftMax layer would be applied to normalize the likelihood to a probability distribution.

Step 4:
Finally, the cross entropy loss is applied to the probability distribution with the ground truth one-hot vector, in our case one-hot vector for word“fox”.

The error is back propagated and the word-embedding and context-embedding layers are updated via gradient descent.

![picture1](/img/formula1.jpg)

The training could be expensive since in the denominator of SoftMax, we need to compute all the inner products between the context embedding for the |V| vocabulary and the center word embedding. This would be O(|V|) time complexity.



That's all, Thank you.

If you encounter any problems, you can open an issue in the **Comment area**.
