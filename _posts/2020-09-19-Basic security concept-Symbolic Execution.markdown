---
layout:     post
title:      "Basic security concept-Symbolic Execution"
subtitle:   " \"Information Security\""
date:       2020-09-19 08:18:00
author:     "Nastul"
header-img: "img/home_194132108.jpg"
tags:
    - InformationSecurity  
---


**符号执行**

一种白盒的静态分析技术，通过输出分析出输入， 比如说数组越界的bug状态，分析出输入值。

但是调用了外部库的函数输入输出并不会直接复制到符号中，所以会阻断此类问题的求解。

经典的解决方法， 基于LLVM的KLEE, 修改调用函数，使其有某个值。

限制输入来解决循环的无限路径问题。