---
layout:     post
title:      "HMM Hidden Markov Model"
subtitle:   " \"Traditional NLP\""
date:       2019-11-30 16:29:00
author:     "Nastul"
header-img: "img/prml1.jpg"
tags:
    - PRML
---
通信的本质就是一个编解码和传输的过程。



随机过程中各个状态的概率分布只与前一个状态有关。




某一个状态只由前一个状态决定，这就是一个一阶马尔可夫模型。而像天气这样，天气状态间的转移仅依赖于前 n 天天气的状态，即状态间的转移仅依赖于前 n 个状态的过程。这个过程就称为n 阶马尔科夫模型.


两个基本假设，三个基本问题。
齐次，观测独立。  概率计算，学习，预测。


1.概率计算问题 输入: 模型$\lambda=(A,B,\pi)$, 观测序列$O=(o_1,o_2,\dots,o_T)$ 输出: $P(O|\lambda)$
2.
学习问题 输入: 观测序列 $O=(o_1,o_2,\dots,o_T)$ 输出: 输出$\lambda=(A,B,\pi)$

3.预测问题, 也称为解码问题(Decoding) 输入: 模型$\lambda=(A,B,\pi)$, 观测序列$O=(o_1,o_2,\dots,o_T)$ 输出: 状态序列 $I=(i_1,i_2,\dots,i_T)$

马尔科夫链： P(st|s1,s2,s3...st-1)=p(st|st-1)
隐马尔可夫模型：<a href="https://www.codecogs.com/eqnedit.php?latex=P(s_{1}s_{2}s_{3}...|o_{1}o_{2}o_{3}...)&space;=&space;P(o_{1}o_{2}o_{3}...|s_{1}s_{2}s_{3}...)P(s_{1}s_{2}s_{3}...)&space;=&space;\prod&space;P(o_{t}|s_{t})P(s_{t}|s_{t-1})" target="_blank"><img src="https://latex.codecogs.com/gif.latex?P(s_{1}s_{2}s_{3}...|o_{1}o_{2}o_{3}...)&space;=&space;P(o_{1}o_{2}o_{3}...|s_{1}s_{2}s_{3}...)P(s_{1}s_{2}s_{3}...)&space;=&space;\prod&space;P(o_{t}|s_{t})P(s_{t}|s_{t-1})" title="P(s_{1}s_{2}s_{3}...|o_{1}o_{2}o_{3}...) = P(o_{1}o_{2}o_{3}...|s_{1}s_{2}s_{3}...)P(s_{1}s_{2}s_{3}...) = \prod P(o_{t}|s_{t})P(s_{t}|s_{t-1})" /></a>



隐马尔可夫模型的三个基本问题：<br>
1.给定模型，如何计算某个特定输出序列的概率 （forward-backward)<br>
2.给定模型和特定输出序列，找到最可能产生这个输出的状态序列(Viterbi Algorithm)<br>
3.给定足够的观测量，估计模型参数(train 问题)<br>


3.st-1 进入 st 的转移概率 Transition probability,  st产生ot的生成概率 Generation Probability。  这些概率被称作隐马尔可夫模型的参数， 估计这个参数过程，就是模型的训练。

p(ot|st) = p(ot,st)/p(st) ....  可以直接通过大量人工标注的数据 依照统计语言模型的训练方法，但是成本太高。

Baum-Welch Algorithm. 寻找最可能的seta.
and EM


朴素贝叶斯模型：P(y|x)=P(y)累乘P(x|y)
要确定一个HMM模型，我们需要知道三个参数
λ(A, B, π) P(y1,y2,y3)=∑q1k∑q2k∑q3kP(y3|q3)×P(q3|q2)×P(y2|q2)×P(q2|q1)×P(y1|q1)×P(q1)

加上时间序列就是动态模型。

![avatar](/img/20191130183748.png)

![avatar](/img/20191130200013.png)
