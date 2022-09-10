---
layout: post
title:  "[WIP]GPU Architecture and GPU Kernels"
date:   2022-09-09 08:34:43 +0000
---
In this post, we will discuss how GPU architecture and GPU kernels look like. First, we will introduce GPU structure, secondly, we will develope a simple GPU kernel and discuss different scenarios. This is an introductory level post, the idea is to get the reader familiar with the architecture and implementation. Also, quick note to mention, I am aware that these technologies are getting improved and changed very frequently, however, I believe, grasping the main logic behind them will be helpful to adapt new versions and developments.  

The Graphics Processing Unit (GPU) is special hardware, that processes data in immensely parallel way, which leads to much higher instruction throughput and memory bandwidth than the CPU within a similar power budget.

# How SKU looks like?

SKU stands for Stock-Keeping Unit, it's usually a synonym with a type of hardware / something in stock. It's mostly used meaning "type of server" (kind-of like AWS's instance types). Generally, SKUs with GPU cards attached have a "host" part and "devices" part. These two parts are connected with PCIe bus.  
![GPU-CPU hybrid platform](/assets/gpu-cpu-hybrid.png)
 
Even though the picture above shows 4 CPU cores in the host part, in general, these SKU's are customizable. In other words, the number of cores and and number of GPUs attached and amount of memory in both sides are not fixed. The main things to remember about this SKUs are

 - We have host part, which consists of CPUs and Memory
 - We have one or more GPUs (each of them called "device") in devices part
 - Each of these device has its memory (In some generation, it is 40G or 80G)
 - There is a memory shared among these devices
 - Host and GPU part are connected via PCIe bus

In addition, these devices has mesh connection between them. That means, all the devices has a direct access to all other devices (via NVLink). This architecture is super efficient in most use cases, such as gradient syncronizing/sharing in deep learing training process. This mesh connections avoid devices to send/receive messages via PCIe bus through host memory (which adds latency and power usage), they just directly talk to each other.
![mesh-connection](/assets/mesh.png) 



 




# Resources:
 - Correction: A Hybrid CPU-GPU Accelerated Framework for Fast Mapping of High-Resolution Human Brain Connectome by Y. Wang et al. 