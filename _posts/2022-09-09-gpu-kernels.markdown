---
layout: post
title:  "[WIP]GPU Architecture and GPU Kernels"
date:   2022-09-09 08:34:43 +0000
---
In this post, we will discuss how GPU architecture and GPU kernels look like. First, we will introduce GPU structure, secondly, we will develope a simple GPU kernel and discuss different scenarios. This is an introductory level post, the idea is to get the reader familiar with the architecture and implementation. Also, quick note to mention, I am aware that these technologies are getting improved and changed very frequently, however, I believe, grasping the main logic behind them will be helpful to adapt new versions and developments.  

The Graphics Processing Unit (GPU) is special hardware, that processes data in immensely parallel way, which leads to much higher instruction throughput and memory bandwidth than the CPU within a similar power budget.

# How SKU looks like?

SKU stands for Stock-Keeping Unit, it's usually a synonym with a type of hardware / something in stock. It's mostly used meaning "type of server" (kind-of like AWS's instance types). Generally, SKUs with GPU cards attached have a "host" part and "devices" part. 
![GPU-CPU hybrid platform](/assets/gpu-cpu-hybrid.png)
 





# Resources:
 - Correction: A Hybrid CPU-GPU Accelerated Framework for Fast Mapping of High-Resolution Human Brain Connectome by Y. Wang et al. 
