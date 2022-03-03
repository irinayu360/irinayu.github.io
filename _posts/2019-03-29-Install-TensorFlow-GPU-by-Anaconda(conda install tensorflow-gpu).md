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


**You can download anaconda [here](https://www.anaconda.com/distribution/#download-section).**

One of the advantage of anaconda is that it can create **isolated environment** in your device, and you can configure any libraries and toolkits in the 'env' without affect other environment. Once you are nor satisfied of your configuration, you can simplily delete the environment.

Note that in you are in **China**, download anaconda might take a long time due to some resons that cannot say. Instead, you can download it from [**Tsinghua mirror**](https://mirror.tuna.tsinghua.edu.cn/help/anaconda/), and install it **manually**.  

After downloading this successfully, try to run the installation file.
For example, if you use ubuntu, you can cd to the path of the sh file and run the following command:

```bash
./Anaconda3-5.3.1-Linux-x86_64.sh
```
***Attention that you should change the command above to your own installation file name.***

Then you will successfully install Anaconda!

## Create new environment by conda

If you are unwilling to create conda environment (maybe because of lazy), you can skip this section. However, I strongly reconmend you to create this **for the convience in the future**.  

Run the command below:
```bash
conda create -n tf
```
![picture1](/img/20190328post.jpg)

'tf' is the name of your new conda environment, you can try other names as your own interest.

For other management you conda env, you can read [this](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html?highlight=environment).

## Install Tensorflow

First, you need to change to the env you have just built by conda:
```bash
source activete tf
```
![picture2](/img/20190328post2.jpg)  

For Chinese users, before starting the installation, you may change the source of conda as the same reason before. For more details, read the webcite of [Tsinghua Mirror](https://mirror.tuna.tsinghua.edu.cn/help/anaconda/).
Chinese users should type in this:
```bash
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```


Afterwards, type in the command to install TensorFlow you need:
```bash
conda install tensorflow-gpu
```
![picture3](/img/20190328post3.jpg)  

If you want to install a specific version of tensorflow-gpu or cpu veison, you can change the command like this:
```bash
conda install tensorflow-gpu=1.10.0  #if you want to install 1.10.0 version
conda install tensorflow  #if you want to install cpu version
```
After anaconda solve the environment, you just need to type in 'y' to confirm the installation.  

Anaconda will **automatically** install other libs and toolkits needed by tensorflow(e.g. CUDA, and cuDNN), so you have no need to worry about this.
--

Type in `python` to enter the python environment.
```python
import tensorflow as tf
tf.__version__
```
When you see the version of tensorflow, such as 1.10.0, you have successfully install it.

That's all, Thank you.

If you encounter any problems, you can open an issue in the **Comment area**.
