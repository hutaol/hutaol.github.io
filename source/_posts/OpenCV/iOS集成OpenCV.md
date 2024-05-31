---
title: iOS集成OpenCV
date: 2024-05-08 21:16:47
tags:
categories: OpenCV
---

## 编译OpenCV

参考：https://zhuanlan.zhihu.com/p/107606884

## iOS集成OpenCV

常见错误

问题一：enum { NO, GAIN, GAIN_BLOCKS };    Expected identifier

只要把`NO`修改成 `NO_EXPOSURE_COMPENSATOR` 或 `NO_EXPOSURE_COMPENSATOR = 0`

问题二：core.hpp header must be compiled as C++ 或 base.hpp header must be compiled as C++

解决：把调用了OpenCV文件的.m文件修改为.mm，以及viewController.m修改为viewController.mm
