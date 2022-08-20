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
A contiguous tensor is a tensor whose elements are stored in a contiguous order without leaving any empty space between them. A tensor created originally is always a contiguous tensor.Now, lets play with a contigous tensor, and make it non-contigous and see how stride is getting affected by this and why.
```
>>> # Create a tensor of shape [4, 3]
>>> x = torch.arange(12).view(4, 3)
>>> x
tensor([[ 0,  1,  2],
        [ 3,  4,  5],
        [ 6,  7,  8],
        [ 9, 10, 11]])
>>> x.stride()
(3, 1)
>>> x.is_contiguous()
True
```

If we look at the strides, we see, that we would have to skip 3 values to go to the new row, while only 1 to go to the next column. That makes sense so far. The values are stored sequentially in memory, i.e. the memory cells should hold the data as [0, 1, 2, 3, ..., 11].


Now lets transpose the tensor, and have again a look at the strides:

```
>>> y = x.t()
>>> y
tensor([[ 0,  3,  6,  9],
        [ 1,  4,  7, 10],
        [ 2,  5,  8, 11]])
>>> y.stride()
(1, 3)
>>> y.is_contiguous()
False
```

First of all, getting transpose of contiguous tensor, makes it non-contiguous. However, the strides are now swapped. In order to go to the next row, we only have to skip 1 value, while 3 to move to the next column. This makes sense, if we recall the memory layout of the tensor:[0, 1, 2, 3, 4, ..., 11]
In order to move to the next column (e.g. from 0 to 3, we would have to skip 3 values.
The tensor is thus non-contiguous anymore!


Now, lets make the tensor contigous, again.

```
>>> y = y.contiguous()
>>> y.stride()
(4, 1)
>>> y.is_contiguous()
True
```

If you call contiguous() on a non-contiguous tensor, a copy will be performed. Otherwise it will be a no-op.

# ReShaping Operations on Tensors
*Reshaping* operations are probably the most important type of tensor operations. Reshaping allows us to change the shape with the same data and number of elements as self but with the specified shape, which means it returns the same data as the specified array, but with different specified dimension sizes

## ReShape
Reshape method of tensor returns a tensor with the same data and number of elements as self, but with the specified shape. When possible, the returned tensor will be a view of input. Otherwise, it will be a copy. Contiguous inputs and inputs with compatible strides can be reshaped without copying.
```
>>> t=torch.arange(12)
>>> t
tensor([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])
>>> a=t.reshape(2,6)
>>> a
tensor([[ 0,  1,  2,  3,  4,  5],
        [ 6,  7,  8,  9, 10, 11]])
>>> t
tensor([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])
>>> a.storage().data_ptr()
140697029066880
>>> t.storage().data_ptr()
140697029066880
>>> torch.equal(a,t)
False
>>> a.reshape(-1)
tensor([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11])
>>> a
tensor([[ 0,  1,  2,  3,  4,  5],
        [ 6,  7,  8,  9, 10, 11]])
```

### View


### Squeezing and Unsquezzing

### Flatten

### Concatenate


# Resources
 - http://blog.ezyang.com/2019/05/pytorch-internals/
 - https://pytorch.org/tutorials/beginner/basics/tensorqs_tutorial.html
 - https://deeplizard.com/learn/video/fCVuiW9AFzY
 - https://discuss.pytorch.org/t/contigious-vs-non-contigious-tensor/30107/2
