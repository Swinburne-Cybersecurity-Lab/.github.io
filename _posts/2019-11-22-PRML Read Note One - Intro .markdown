---
layout:     post
title:      "PRML READ NOTE ONE - Introduction"
subtitle:   " \"Hello Coding, Hello World \""
date:       2019-11-22 23:35:00
author:     "Nastul"
header-img: "img/prml1.jpg"
tags:
    - PRML
---


<br>
I studied statistical machine learning this semester. But a lot of knowledge is not well understood. So plan to look at 'Pattern Recognition and Machine Learning' again and take notes.



> 正确分类新样本的能力叫做泛化（generalization) 中心问题
>
>pre-processed 原始输入向量映射到新的空间 -> 让问题更容易解，有时这个过程也叫做特征提取  feature extraction
>
>为了加速计算，有时也会需要进行预处理去找到有用的特征
>
>每个输入向量分配到有限个离散的标签是分类问题 classification
>
>输出由一个或者多个连续变量组成是回归问题  regression
>
>unsupervised learning  -  clustering  - density estimation (其实就是求参数分布)  -  visualization 
>
>supervised learning - 输入向量对应到标签向量
>
>reinforcement learning  通过选择动作，使得获得的奖励最大化， 这中间设计两个事件的平衡， exploration and exploitation
>
>超参数是控制模型参数分布的参数
>
>验证集小的时候可以使用交叉验证， cross validation 但是会带来训练次数增加和参数探索次数增加的问题
    

多项式曲线拟合： 
<a href="https://www.codecogs.com/eqnedit.php?latex=y(x,w)=\sum&space;^M&space;_{j=0}w_{j}x^{j}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?y(x,w)=\sum&space;^M&space;_{j=0}w_{j}x^{j}" title="y(x,w)=\sum ^M _{j=0}w_{j}x^{j}" /></a><br>
误差函数：<a href="https://www.codecogs.com/eqnedit.php?latex=E(w)=&space;\frac{1}{2}&space;\sum_{n=1}&space;^{N}&space;(y(x,w)-t_{n})^{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?E(w)=&space;\frac{1}{2}&space;\sum_{n=1}&space;^{N}&space;(y(x,w)-t_{n})^{2}" title="E(w)= \frac{1}{2} \sum_{n=1} ^{N} (y(x,w)-t_{n})^{2}" /></a>
<br>是MLE的特殊情况， 它的一次导数是线性的，所以最小值有一个唯一的解 w*

RMS 根均方误差：<a href="https://www.codecogs.com/eqnedit.php?latex=E_{RMS}=\sqrt{2E(w^{*})/N}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?E_{RMS}=\sqrt{2E(w^{*})/N}" title="E_{RMS}=\sqrt{2E(w^{*})/N}" /></a><br> N是为了用相同的基数去对比不同大小的数据集，平方根保证了它与目标变量t使用相同的规模和单位进行度量
<a href="https://www.codecogs.com/eqnedit.php?latex=&plus;\left&space;\|w&space;\right&space;\|^{2}_{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?&plus;\left&space;\|w&space;\right&space;\|^{2}_{2}" title="+\left \|w \right \|^{2}_{2}" /></a> 是误差项， ridge  
<a href="https://www.codecogs.com/eqnedit.php?latex=\left&space;\|w&space;\right&space;\|^{2}_{2}&space;=&space;w^{T}w=w_{0}^{2}&plus;w_{1}^{2}&plus;w_{2}^{2}&plus;...&plus;w_{M}^{2}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?\left&space;\|w&space;\right&space;\|^{2}_{2}&space;=&space;w^{T}w=w_{0}^{2}&plus;w_{1}^{2}&plus;w_{2}^{2}&plus;...&plus;w_{M}^{2}" title="\left \|w \right \|^{2}_{2} = w^{T}w=w_{0}^{2}+w_{1}^{2}+w_{2}^{2}+...+w_{M}^{2}" /></a>
<br> shrinkage 收缩方法减小系数的值， 在神经网络中也被叫做 weight decay 权值衰减.

hold-out set /  validation set 会浪费训练集，所以需要考虑其他的方法去验证

###  概率论基础 Probability  ###

Joint Probability  p(x,y)<br>
conditional probability:  p(x|y)<br>
independent: p(x,y)=p(x)p(y)<br>
sum rule:<a href="https://www.codecogs.com/eqnedit.php?latex=p(x)=\sum&space;_{y}p(x,y)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?p(x)=\sum&space;_{y}p(x,y)" title="p(x)=\sum _{y}p(x,y)" /></a>

product rule:<a href="https://www.codecogs.com/eqnedit.php?latex=p(x,y)=p(y|x)p(x)" target="_blank"><img src="https://latex.codecogs.com/gif.latex?p(x,y)=p(y|x)p(x)" title="p(x,y)=p(y|x)p(x)" /></a>

bayes' theorm: <a href="https://www.codecogs.com/eqnedit.php?latex=p(y|x)=\frac{p(x|y)p(y)}{p(x)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?p(y|x)=\frac{p(x|y)p(y)}{p(x)}" title="p(y|x)=\frac{p(x|y)p(y)}{p(x)}" /></a>
<a href="https://www.codecogs.com/eqnedit.php?latex=p(y|x)=p(x,y)/p(x)=\frac{p(x|y)p(y)}{p(x)}=\frac{p(x|y)p(y)}{\sum&space;_y&space;p(x|y)p(y)}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?p(y|x)=p(x,y)/p(x)=\frac{p(x|y)p(y)}{p(x)}=\frac{p(x|y)p(y)}{\sum&space;_y&space;p(x|y)p(y)}" title="p(y|x)=p(x,y)/p(x)=\frac{p(x|y)p(y)}{p(x)}=\frac{p(x|y)p(y)}{\sum _y p(x|y)p(y)}" /></a>

p.d.f ------ c.d.f
![avatar](/img/fullsizerender1.jpg)










