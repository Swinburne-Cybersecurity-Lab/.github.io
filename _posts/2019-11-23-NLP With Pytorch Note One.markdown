---
layout:     post
title:      "NLP With Pytorch Note One"
subtitle:   " \"Hello Coding, Hello World \""
date:       2019-11-23 16:45:00
author:     "Nastul"
header-img: "img/prml1.jpg"
tags:
    - PRML
---
Some Definitions:<br>
• Words<br>
&nbsp;&nbsp;&nbsp;&nbsp;* Sequence of characters with a meaning and/or function<br>
• Sentence<br>
&nbsp;&nbsp;&nbsp;&nbsp;* “The student is enrolled at the University of Melbourne.”<br>
• Word token: each instance of “the” in the sentence
above.<br>
• Word type: the distinct word “the”.<br>
&nbsp;&nbsp;&nbsp;&nbsp;* Lexicon: a group of word types.<br>
• Document: one or more sentences.<br>
• Corpus: a collection of documents.<br><br>

**Preprocessing is the first step.**<br>
• Remove unwanted formatting (e.g. HTML)<br>
• Segment structure (e.g. sentences)<br>
• Tokenise words<br>
• Normalise words<br>
• Remove unwanted words<br>

**Sentence segmentation**
• Naïve approach: break on sentence punctuation
([.?!])<br>
&nbsp;&nbsp;&nbsp;&nbsp;* But periods are used for abbreviations!<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;(U.S. dollar, …, Yahoo! as a word)<br>
• Second try: use regex to require capital ([.?!] [A-Z])<br>
&nbsp;&nbsp;&nbsp;&nbsp;* But abbreviations often followed by names (Mr. Brown)<br>
• Better yet: have lexicons<br>
&nbsp;&nbsp;&nbsp;&nbsp;* But difficult to enumerate all names and abbreviations<br>
• State-of-the-art uses machine learning, not rules<br>

**Tokenisation: English** <br>
• Naïve approach: separate out alphabetic strings (\w+)<br>
• Abbreviations (U.S.A.)<br>
• Hyphens (merry-go-round vs. well-respected vs. yes-but)<br>
• Numbers (1,000,00.01)<br>
• Dates (3/1/2016)<br>
• Clitics (n’t in can’t)<br>
• Internet language (http://www.google.com, #metoo, :-))<br>
• Multiword units (New Zealand)
<br>

**Word normalisation**<br>
• Lower casing (Australia -> australia)<br>
• Removing morphology<br>
• Correcting spelling<br>
• Expanding abbreviations<br>

**Inflectional Morphology**  -  **Lemmatisation** - **Derivational morphology** - **Stemming** <br>

Term-document matrix, we can Measuring similarity with cosine 
cos(a,b)= a·b/|a|x|b|
![avatar](/img/20191123174140.png)


由于自由文本并不能被计算机直接处理，我们需要将其编码成计算机能够理解的形式。
<br>
One-Hot Representation 每一个单词或者字母使用一个维度表示
![avatar](/img/bf2571d77271c27a0bb65f60aa4926c0.jpg)
但是这样表示会存在有不同意义的单词被相同的向量表示<br>
另一种表示形式：<br>
术语频率(TF)和术语频率反转文档频率(TF-IDF)<br>
TF Representation 术语出现的频率<br>


TF-IDF Representation<br>
TF表示对更频繁的单词进行加权，IDF表示惩罚常见的符号，并奖励向量表示中的罕见符号。<br>
TF-IDF分数就是TF(w) * IDF(w)的乘积。<br>

![avatar](/img/20191123174604.png)

Calculate the similarity between the query pseudodocument
and each document in the collection<br>
Rank documents by decreasing similarity with cosine<br>

**BM25 most widely used method in IR**<br>

**Index**<br>
• Imagine we pre-compute the TF*IDF vectors for all documents, and their vector lengths (for normalisation)<br>
• These do not change from query to query, so save time by pre-calculating their values<br>
• But still need to iterate over every document…<br>
**Term-wise processing**:when measuring document similarity, only terms occurring in both documents contribute to cosine score, so with the query as a pseudo-document need only consider terms that are. 
**Inverted index comprises** 行变列 ， aka posting list

**Index compression and efficient query processing**<br>

**Compression Principles**<br>
Entropy H:<a href="https://www.codecogs.com/eqnedit.php?latex=H(T)=-\sum&space;\frac{f_{s}}{n}log_{2}\frac{f_{s}}{n}" target="_blank"><img src="https://latex.codecogs.com/gif.latex?H(T)=-\sum&space;\frac{f_{s}}{n}log_{2}\frac{f_{s}}{n}" title="H(T)=-\sum \frac{f_{s}}{n}log_{2}\frac{f_{s}}{n}" /></a>
where fs is the frequency of symbol s in T and n is the length of T.

![avatar](/img/20191123193419.png)

**WAND**

**Target Encoding**

**Computational Graphs**<br>
监督学习(训练)范式概括为数据流架构，模型(数学表达式)对输入进行转换以获得预测，损失函数(另一个表达式)提供反馈信号来调整模型的参数。利用计算图数据结构可以方便地实现该数据流。从技术上讲，计算图是对数学表达式建模的抽象。

**PyTorch Basics**<br>
PyTorch实现了一种“tape-based automatic differentiation”方法，允许我们动态定义和执行计算图形。这对于调试和用最少的努力构建复杂的模型非常有帮助。
> 
> 动态 VS 静态计算图 像Theano、Caffe和TensorFlow这样的静态框架需要首先声明、编译和执行计算图。虽然这会导致非常高效的实现(在生产和移动设置中非常有用)，但在研究和开发过程中可能会变得非常麻烦。像Chainer、DyNet和PyTorch这样的现代框架实现了动态计算图，从而支持更灵活的命令式开发风格，而不需要在每次执行之前编译模型。动态计算图在建模NLP任务时特别有用，每个输入可能导致不同的图结构。

0阶张量就是一个数字，或者标量。一阶张量(一阶张量)是一个数字数组，或者说是一个向量。类似地，二阶张量是一个向量数组，或者说是一个矩阵。因此，张量可以推广为标量的n维数组

**Creating Tensors** in pytorch<br>

    import torch
    torch.Tensor(2, 3)
	describe(torch.rand(2, 3))   # uniform random
	describe(torch.randn(2, 3))  # random normal

我们还可以创建张量，所有张量都用相同的标量填充。对于创建0或1张量，我们有内置函数，对于填充特定值，我们可以使用fill()方法。任何带有下划线( )的PyTorch方法都是指就地(in place)操作;也就是说，它在不创建新对象的情况下就地修改内容

	x = torch.ones(2, 3)
	x.fill_(5)

Creating and initializing a tensor from lists

	x = torch.Tensor([[1, 2, 3],  
                      [4, 5, 6]])

值可以来自列表(如前面的示例)，也可以来自NumPy数组。当然，我们也可以从PyTorch张量变换到NumPy数组。注意，这个张量的类型是一个double张量，而不是默认的FloatTensor。这对应于NumPy随机矩阵的数据类型float64


每个张量都有一个相关的类型和大小。使用torch时的默认张量类型。张量构造函数是torch.FloatTensor。但是，可以在初始化时指定张量，也可以在以后使用类型转换方法将张量转换为另一种类型(float、long、double等)。有两种方法可以指定初始化类型，一种是直接调用特定张量类型(如FloatTensor和LongTensor)的构造函数，另一种是使用特殊的方法torch。张量，并提供dtype，

	x = torch.FloatTensor([[1, 2, 3],  
                           [4, 5, 6]])
	x = x.long()

**Tensor Operations**<br>
还有一些运算可以应用到张量的特定维数上。正如您可能已经注意到的，对于2D张量，我们将行表示为维度0，列表示为维度1

	torch.sum(x, dim=0)
	torch.sum(x, dim=1)
	torch.transpose(x, 0, 1)

**Indexing, slicing, and joining**
L[0:3]表示，从索引0开始取，直到索引3为止，但不包括索引3。即索引0，1，2，正好是3个元素。如果第一个索引是0，还可以省略：
	x[:1, :2]
非连续：
	indices = torch.LongTensor([0, 2])
	torch.index_select(x, dim=1, index=indices)
连接函数连接张量：
	torch.cat([x, x], dim=0)
	torch.stack([x, x])

	x2[:, 1] += 1
	torch.mm(x1, x2)

**Tensors and Computational Graphs**
PyTorch张量类封装了数据(张量本身)和一系列操作，如代数操作、索引操作和整形操作。然而,1-15所示的例子,当requires_grad布尔标志被设置为True的张量,记账操作启用,可以追踪的梯度张量以及梯度函数,这两个需要基于促进梯度学习讨论“监督学习范式”
	x = torch.ones(2, 2, requires_grad=True)
	x.grad


**CUDA Tensors**
它将张量从CPU传输到GPU，同时维护其底层类型。PyTorch中的首选方法是与设备无关，并编写在GPU或CPU上都能工作的代码。在下面的代码片段中，我们首先使用torch.cuda.is_available()检查GPU是否可用，然后使用torch.device检索设备名。然后，将实例化所有未来的张量，并使用.to(device)方法将其移动到目标设备。


	torch.cuda.is_available()
	device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
	x = torch.rand(3, 3).to(device)

要对CUDA和非CUDA对象进行操作，我们需要确保它们在同一设备上。如果我们不这样做，计算就会中断，如下面的代码片段所示。例如，在计算不属于计算图的监视指标时，就会出现这种情况。当操作两个张量对象时，确保它们在同一个设备上

请记住，将数据从GPU来回移动是非常昂贵的。因此，典型的过程包括在GPU上执行许多并行计算，然后将最终结果传输回CPU。这将允许您充分利用gpu。如果您有几个CUDA-visible设备(即，最佳实践是在执行程序时使用CUDA_VISIBLE_DEVICES环境变量，

	CUDA_VISIBLE_DEVICES=0,1,2,3 python main.py
