---
layout:     post
title:      "PRML Read Note Two - Prob Distribution "
subtitle:   " \"Hello Coding, Hello World \""
date:       2019-11-23 00:30:00
author:     "Nastul"
header-img: "img/prml1.jpg"
tags:
    - PRML
---


<br>
频率派学家的观点中，我们通过最优化某些准则来确定参数的具体值，贝叶斯观点中，给定观察的数据，引入参数的先验分布，是用贝叶斯定理来计算后验分布。<br>
在这里使用了共轭先验的概念，conjugate prior, 使得后验分布与先验相同，参数方法的一个限制是具体了分布的函数形式，另一种替代方法是非参数密度估计，依赖于数据的规模，这里的参数用于控制模型的复杂度而不是分布的形式。 - 直方图，最近邻，核函数。<br>
伯努利分布：
<a href="https://www.codecogs.com/eqnedit.php?latex=Bern(x|u)=u^{x}(1-u)^{1-x}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?Bern(x|u)=u^{x}(1-u)^{1-x}" title="Bern(x|u)=u^{x}(1-u)^{1-x}" /></a>

关于u的似然函数：
<a href="https://www.codecogs.com/eqnedit.php?latex=p(D|u)=\prod_{n=1}^{N}&space;p(x_{n}|u)=\prod_{n=1}^{N}&space;u^{x_{n}}(1-u)^{1-x_{n}}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?p(D|u)=\prod_{n=1}^{N}&space;p(x_{n}|u)=\prod_{n=1}^{N}&space;u^{x_{n}}(1-u)^{1-x_{n}}" title="p(D|u)=\prod_{n=1}^{N} p(x_{n}|u)=\prod_{n=1}^{N} u^{x_{n}}(1-u)^{1-x_{n}}" /></a>

![avatar](/img/fullsizerender.jpg)








