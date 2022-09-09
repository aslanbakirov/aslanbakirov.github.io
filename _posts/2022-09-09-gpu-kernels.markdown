---
layout: post
title:  "[WIP]GPU Architecture and GPU Kernels"
date:   2022-09-09 08:34:43 +0000
---
In this post, we will discuss how GPU architecture and GPU kernels look like. First, we will introduce GPU structure, secondly, we will develope a simple GPU kernel and discuss diffirent scenarios. This post is introductory level, idea is to get the reader familiar with the architecture and implementation

The Graphics Processing Unit (GPU) is special hardware, that processes data in immensely parallel way, which leads to much higher instruction throughput and memory bandwidth than the CPU within a similar power budget.

