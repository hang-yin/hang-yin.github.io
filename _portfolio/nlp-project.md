---
title: "Graph Convolutional Network for Sentiment Analysis"
author_profile: true
key: 1
excerpt: "NLP, edge-conditioned GCN, Tensorflow"
header:
  teaser: /assets/images/nlp_pipeline.jpg
---

{% comment %} 
sidebar:
  - title: "Role"
    image: http://placehold.it/350x250
    image_alt: "logo"
    text: "Designer, Front-End Developer"
  - title: "Responsibilities"
    text: "Reuters try PR stupid commenters should isn't a business model"
{% endcomment %} 

This project explores combining dependency parsing with pre-trained language embedding models using edge-conditioned graph convolution networks.

## Purpose:
SOTA sentiment classification approaches rely on very large statistical language models that perform well but difficult to interpret. By training and representing language models as graphs with separable semantic and syntactical features, we can better understand how language models make decisions and build models that reflect human understanding of language. 

## Methods:
The theory of dependency grammar represents the syntactical structure of sentences as a directed graph where the nodes as words and the edges are relations between the words. Each edge describes how the target word, named the dependent, modifies the source word, named the head. By combining dependency trees and pre-trained language models, we can represent sentences as trees where the nodes are n-dimensional vector representations of words, and the edges are the dependency relations. By using Edge-Conditioned Graph Convolution Networks, we aim to combine the structural, syntactic, and semantic information from a sentence for the task of sentiment classification. 


![]({{ site.url }}{{ site.baseurl }}/assets/images/nlp_pipeline.jpg)

## Results:
Edge-Conditioned GCN (87.36) outperforms baselines on the IMDB binary classification task. However, one-hot encoding of edge types is insufficient for learning or utilizing different types of depenendcy relations.

## Conclusion:
We demonstrated that it is possible to perform sentiment classification while integrating syntactical and semantic information in a graphical way. However, the task of learning and integrating the representations of dependency relation types is still unsolved.

Check out our paper [here](https://raw.githubusercontent.com/hang-yin/portfolio/gh-pages/assets/nlp-paper.pdf).

[Github repo](https://github.com/xiaojoey/CS397Project)