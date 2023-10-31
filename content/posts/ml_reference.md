---
title: "ML Reference"
date: 2023-07-19T11:01:42+01:00
tags: ['ML']
draft: false
---

This page is an annotated reference of machine learning papers and related stuff.
There are similar lists all over the internet and this list will not be complete, nor up-to-date.
These are topics I am (or was) interested in or that I think that will be useful later.

Ofcourse, after starting this list I ran into the
[Methods](https://paperswithcode.com/methods) section of [Papers with Code](https://paperswithcode.com).
Highly recommended.
Another favorite of mine is [NLP-progress](http://nlpprogress.com/).

# Overview

## On the Dangers of Stochastic Parrots: Can Language Models Be Too Big?

* [DOI: 10.1145/3442188.3445922](https://10.1145/3442188.3445922)
* year: 2021

Overview of development of LLMs and the risc of depending on them.
Famous models with parameter counts, and the datasets they are trained on.
Also Natural Language Understanding (NLU) is not General Inteligence

# Gathering data

## Common crawl

* [URL](https://commoncrawl.org/)

Large collection of texts from the internet to train language models.

The Colossal Clean Crawled Corpus (c4) is the common crawl dataset, but then
cleaned up and ['bad words'](https://github.com/LDNOOBW/List-of-Dirty-Naughty-Obscene-and-Otherwise-Bad-Words/tree/master) removed.

# Pre-processing data

# Network design

## Attention is all you need

* [URL](https://dl.acm.org/doi/10.5555/3295222.3295349)
* year: 2017

The Transformer network with self-attention.

## Transformers are RNNs: Fast Autoregressive Transformers with Linear Attention

* [DOI: 10.48550/arXiv.2006.16236](https://doi.org/10.48550/arXiv.2006.16236)
* [URL](https://linear-transformers.com/)
* year: 2020

Linearized version of a Transformer (which is quadratic in the memory length).

### ReZero is All You Need: Fast Convergence at Large Depth

* [DOI: 10.48550/arXiv.2003.04887](https://doi.org/10.48550/arXiv.2003.04887)
* year: 2021

Activation function good for training deep networks -- the trick can also be used for ReLU, GeLU etc.

# Training

## Initialization

### Understanding the difficulty of training deep feedforward neural networks

* [URL](http://proceedings.mlr.press/v9/glorot10a.html)

Glorot and Xavier uniform / random initialization of weights and biases

## Activation

### Gaussian Error Linear Units (GELUs)

* [DOI: 10.48550/arXiv.1606.08415](https://doi.org/10.48550/arXiv.1606.08415)
* year: 2023 (first 2016)

Activation function that mimicks dropout; assumes layers are normalized.

## Loss functions

### Focal Loss for Dense Object Detection

* [DOI: 10.48550/arXiv.1708.02002](https://doi.org/10.48550/arXiv.1708.02002)
* year: 2018

Lossfunction that focusses on uncertain items,
and on mistakes where the certainty is high.
Similar to cross-entropy.

## Supervised Contrastive Learning

* [DOI: 10.48550/arXiv.2004.11362](https://doi.org/10.48550/arXiv.2004.11362)
* year: 2021 (2020)

## Backpropagation

### Adam: A Method for Stochastic Optimization

* [DOI: 10.48550/arXiv.1412.6980](https://doi.org/10.48550/arXiv.1412.6980)
* year: 2015

Adaptive moment estimation; an extension to Stochastic Gradient Descent.
Simple, efficient, and mostly good enough.

# Evaluation

## Rogue scores

* [URL](https://aclanthology.org/2023.acl-long.107/)
* year: 2023

Reproducability of ML papers using ROGUE scores is very low.
Blaimed on bad software implementations, and bad statistical practices.

## Silhouettes: A graphical aid to the interpretation and validation of cluster analysis

* [URL](https://www.sciencedirect.com/science/article/pii/0377042787901257)
* [DOI 10.1016/0377-0427(87)90125-7](https://doi.org/10.1016/0377-0427(87)90125-7)
* [scikit-learn.org](https://scikit-learn.org/stable/auto_examples/cluster/plot_kmeans_silhouette_analysis.html)

A score between -1 (bad, overlapping) and 1 (perfect, compact and clearly separated) for evaluating (unsupervised)
clustering. Looks at within-cluster and between cluster distances.

## Comparing Clusterings – an information based distance

* [URL](https://www.sciencedirect.com/science/article/pii/S0047259X06002016)
* [DOI 10.1016/j.jmva.2006.11.013](https://doi.org/10.1016/j.jmva.2006.11.013)

VI, variation of information, is a score to compare clusterings.
Contrary to many scores, this one really is a metric.

## On the Surprising Behavior of Distance Metrics in High Dimensional Space

* [DOI 10.1007/3-540-44503-X_27](https://doi.org/10.1007/3-540-44503-X_27)

In high-dimensional spaces, in this paper that's 20 or higher, traditional
distances do not mean much anymore.
Manhattan distance (L1) or even L0.1 can perform much better.

# Hyperparameter tuning

# Inference

# Frameworks

## I like to work with

### PyTorch

* [DOI: 10.5555/3454287.3455008](https://dl.acm.org/doi/10.5555/3454287.3455008)
* [URL](https://pytorch.org/)

The current go-to framework in python for machine learning.

### Tensorboard

## Undecided

## I prefer not to work with

### Tensorflow

* [URL](https://www.tensorflow.org/)

Alternative to pytorch.
Had some issues in the past with networks no longer working after some time.



