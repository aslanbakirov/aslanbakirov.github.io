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

The lay out of the tensor in the physical representaiton is stored in *layout* field of Tensor object. Some of the popular layouts are *strided*, *sparse*, etc. In this post, I will only talk about **strided** layout to just give one example in action. 


Strides helps us to translate logical view to physical view. In other words, if you want to read any particular element(s) of your tensor (ex: tensor[2,3]), stride helps you how to find this element in the physical storage (memory). Stride is the jump necessary to go from one element to the next one in the specified dimension. A tuple of all strides is returned when no argument is passed in. Otherwise, an integer value is returned as the stride in the particular dimension. They basically tell us, how many “steps” we skip in memory to move to the next position along a certain axis.

```
>>> t= torch.tensor([[1,1,1,1],
...                  [2,2,2,2],
...                  [3,3,3,3]], dtype=torch.int32)
>>> t.stride()
(4, 1)
>>> t.stride(0)
4
>>> t.stride(1)
1
>>> t.shape
torch.Size([3, 4])
```
In the example above, our first dimension is row, second dimension is column. So, (4,1) means that, to reach to the next row, you have to skip 4 elements, to reach to the next column, you have to skip one elements(basically next element). And, if you want to find a particular element in the memory, you multiple each index with the respective stride for that dimension and sum them al together. Check the example in the image below.
![logical-to-physical](/assets/stride.png)


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
