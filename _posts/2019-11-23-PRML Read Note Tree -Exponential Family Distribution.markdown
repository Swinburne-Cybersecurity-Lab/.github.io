---
layout:     post
title:      "PRML Read Note Tree -Exponential Family Distribution"
subtitle:   " \"Traditional NLP\""
date:       2019-11-23 20:50:00
author:     "Nastul"
header-img: "img/prml1.jpg"
tags:
    - PRML
---
**Exponential Family Distribution**

可以划分成指数形式的分布：p(x|\eta )=h(x)g(\eta )exp(\eta ^{T}u(x))

确保了概率分布是归一化的。

伯努利分布，写成指数的对数，得到的u 就是logistic sigmoid函数，

多项式分布-> softmax,归一化指数

1.充分统计量  2.共轭先验（后验与先验有一样的分布）   3.无信息先验（最大熵）

![avatar](/img/20191202170057.jpg)