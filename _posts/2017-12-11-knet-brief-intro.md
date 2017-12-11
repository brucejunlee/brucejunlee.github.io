---
layout: post
title: "Knet: A Brief Introduction"
author: "李军"
categories: journal
tags: [julia, knet, deep learning]
image:
  feature:
  teaser:
  credit: 
  creditlink: ""
---

## 1 引言

Knet (pronounced "kay-net") is the Koç University deep learning framework implemented in Julia by Deniz Yuret and collaborators. Knet uses dynamic computational graphs generated at runtime for automatic differentiation of (almost) any Julia code. This allows machine learning models to be implemented by only describing the forward calculation (i.e. the computation from parameters and data to loss) using the full power and expressivity of Julia. The implementation can use helper functions, loops, conditionals, recursion, closures, tuples and dictionaries, array indexing, concatenation and other high level language features, some of which are often missing in the restricted modeling languages of static computational graph systems like Theano, Torch, Caffe and Tensorflow. GPU operation is supported by simply using the KnetArray type instead of regular Array for parameters and data. High performance is achieved using custom memory management and efficient GPU kernels.

## 2 特性

## 3 操作

## 4 应用

## References