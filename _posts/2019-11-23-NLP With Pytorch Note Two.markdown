---
layout:     post
title:      "NLP With Pytorch Note Two"
subtitle:   " \"Traditional NLP\""
date:       2019-11-23 20:50:00
author:     "Nastul"
header-img: "img/prml1.jpg"
tags:
    - PRML
---
**Corpora, Tokens, and Types**
原始文本是字符(字节)序列，但是大多数时候将字符分组成连续的称为令牌(Tokens)的连续单元是有用的。在英语中，令牌(Tokens)对应由空格字符或标点分隔的单词和数字序列。将文本分解为令牌(Tokens)的过程称为令牌化(tokenization)。世界语的句子,”Maria frapis la verda sorĉistino,“1有六个令牌。令牌化可能比简单地基于非字母数字字符拆分文本更加复杂.


使用nltk处理令牌：
	from nltk.tokenize import TweetTokenizer

	tokenizer = TweetTokenizer()
	tokenizer.tokenize(tweet.lower())

词可以区分为内容词和停止词，Unigrams, Bigrams, Trigrams, …, Ngrams
Lemmas and Stems - Lemmas是单词的词根形式。这种简化称为lemmatization

**Categorizing Sentences and Documents**

**Categorizing Words: POS Tagging**
我们可以将标记的概念从文档扩展到单个单词或标记。分类单词的一个常见示例是词性标注
	nlp = spacy.load(‘en’)
	doc = nlp(u"Mary slapped the green witch.")
	token.pos_


**Categorizing Spans: Chunking and Named Entity Recognition**
通常，我们需要标记文本的范围;即，一个连续的多令牌边界。例如，“Mary slapped the green witch.”我们可能需要识别其中的名词短语(NP)和动词短语(VP)。这称为分块(Chunking)或浅解析(Shallow parsing)。浅解析的目的是推导出由名词、动词、形容词等语法原子组成的高阶单位。如果没有训练浅解析模型的数据，可以在词性标记上编写正则表达式来近似浅解析。幸运的是，对于英语和最广泛使用的语言来说，这样的数据和预先训练的模型是存在的
	doc.noun_chunks


**Structure of Sentences**
解析树(Parse tree)表示句子中不同的语法单元在层次上是如何相关的。图2-6中的解析树显示了所谓的成分解析。另一种可能更有用的显示关系的方法是使用依赖项解析(dependency parsing)


**Word Senses and Semantics**
相同的单词不同的语义。

**Perceptron: The Simplest Neural Network**
线性运算 称为仿射变换


**Sigmoid** sigmoid函数饱和(即，产生极值输出)非常快，对于大多数输入。这可能成为一个问题，因为它可能导致梯度变为零或发散到溢出的浮点值。这些现象分别被称为消失梯度问题和爆炸梯度问题。因此，在神经网络中，除了在输出端使用sigmoid单元外，很少看到其他使用sigmoid单元的情况，在输出端，压缩属性允许将输出解释为概率。

**Tanh** tanh激活函数是sigmoid在外观上的不同变体,映射一个实值集合从(-∞,+∞)到(-1,+1)范围

**ReLU** ReLU(发音为ray-luh)代表线性整流单元。这可以说是最重要的激活函数。事实上，我们可以大胆地说，如果没有使用ReLU，许多最近在深度学习方面的创新都是不可能实现的。对于一些如此基础的东西来说，神经网络激活函数的出现也是令人惊讶的。它的形式也出奇的简单: f(x)=max(0,x) 因此，ReLU单元所做的就是将负值裁剪为零

ReLU的裁剪效果有助于消除梯度问题，随着时间的推移，网络中的某些输出可能会变成零，再也不会恢复。这就是所谓的“dying ReLU”问题。为了减轻这种影响，提出了Leaky ReLU或 Parametric ReLU (PReLU)等变体，其中泄漏系数a是一个可学习参数: f(x)=max(x,ax)

**Softmax** 激活函数的另一个选择是softmax。与sigmoid函数类似，softmax函数将每个单元的输出压缩为0到1之间。然而，softmax操作还将每个输出除以所有输出的和，从而得到一个离散概率分布，除以k个可能的类。结果分布中的概率总和为1。这对于解释分类任务的输出非常有用，因此这种转换通常与概率训练目标配对，例如分类交叉熵，

**Loss Functions**

**Mean Squared Error Loss**
MSE就是预测值与目标值之差的平方的平均值。还有一些其他的损失函数可以用于回归问题，例如平均绝对误差(MAE)和均方根误差(RMSE)，但是它们都涉及到计算输出和目标之间的实值距离

	mse_loss = nn.MSELoss()
	loss = mse_loss(outputs, targets)
	

**Categorical Cross-Entropy Loss**分类交叉熵损失(categorical cross-entropy loss)通常用于多类分类设置，其中输出被解释为类隶属度概率的预测。目标(y)是n个元素的向量，表示所有类的真正多项分布。如果只有一个类是正确的，那么这个向量就是one hot向量。网络的输出(ŷ)也是一个向量n个元素,但代表了网络的多项分布的预测。分类交叉熵将比较这两个向量(y,ŷ)来衡量损失

	ce_loss = nn.CrossEntropyLoss()
**Binary Cross-Entropy**

	bce_loss = nn.BCELoss()


PyTorch库为优化器提供了几种选择。随机梯度下降法(SGD)是一种经典的选择算法，但对于复杂的优化问题，SGD存在收敛性问题，往往导致模型较差。当前首选的替代方案是自适应优化器，例如Adagrad或Adam，它们使用关于更新的信息。在下面的例子中，我们使用Adam，但是它总是值得查看几个优化器。对于Adam，默认的学习率是0.001。对于学习率之类的超参数，总是建议首先使用默认值，除非您从论文中获得了需要特定值的秘诀。

**perceptron**
