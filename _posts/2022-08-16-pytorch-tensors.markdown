---
layout: post
title:  "[WIP]Tensors and Reshaping operations in PyTorch"
date:   2022-08-16 08:34:43 +0000
---
In this post, we will talk about what is the tensor, how it is stored in memory, and what reshaping operations we can apply on tensors. 

# Tensors
The tensor is the central data structure in Pytorch. Tensor is an n-dimensional data structure that contains some data in scalar type. Some of the types are boolean, integer and float. Imagine tensor as consisting of some data and some metadata describing its size/dimension, data type and where it is stored.

# Tensor Stride/Storage
We can imagine tensor as a combination of two parts: logical and physical. Logical part is how we represent it, physical part is how it is actually stored on our computersThe most common physical representation is to lay out each element of the tensor contigously in the memory. For example, in the example below, the tensor contains 32-bit integers,each integer lies int he physical address, each offset four bytes from each other.
![Tensor Representation](/assets/tensor.png).


### Contigous() vs non-contigous()

# ReShaping Operations on Tensors

### ReShape

### View

### Squeezing and Unsquezzing

### Flatten

### Concatenate


# Resources
 - http://blog.ezyang.com/2019/05/pytorch-internals/
 - https://pytorch.org/tutorials/beginner/basics/tensorqs_tutorial.html
 - https://deeplizard.com/learn/video/fCVuiW9AFzY
