---
layout:     post
title:      "NLP Pytorch Linear Reg"
subtitle:   " \"Traditional NLP\""
date:       2019-11-30 15:20:00
author:     "Nastul"
header-img: "img/prml1.jpg"
tags:
    - PRML
---
**In Pytorch**<br>
写了两次， 第一次数据量大的时候就会出现loss nan， 原因是因为没有做特征缩放，导致爆炸。
特征缩放，可以都直接映射到[0,1] 但是会存在 sensitive to outlier

```python
import matplotlib.pyplot as plt
import numpy as np
import torch
import torch.nn as nn
import torch.nn.functional as F
import torch.optim as optim
from sklearn.datasets import make_classification
%matplotlib inline
#定义模型
class Model(nn.Module):
    def __init__(self):
        super(Model, self).__init__()
        self.linear = torch.nn.Linear(1, 1) # One in and one out

    def forward(self, x):
        y_pred = self.linear(x)
        return y_pred

model = Model()	

#打印模型参数
for i in model.named_parameters():
	print(i)

#生成数据集
x_set = [ [float(i)] for i in range(0,100)]
y_set = torch.tensor( [x[0]*2.5 + torch.tensor(np.random.normal(0,5,1))  for x in x_set])

#打印数据集
import matplotlib.pyplot as plt
#plt.plot(x_set,y_set)
plt.scatter(x_set,y_set.numpy())
plt.show()

#归一化
x_nor = np.array(x_set)
x_nor = x_nor/99
y_nor = (y_set - y_set[0]) / (y_set[99]-y_set[0])

#打印数据集
import matplotlib.pyplot as plt
#plt.plot(x_set,y_set)
plt.scatter(x_nor,y_nor.numpy())
plt.show()
```


```python
x_tensor = torch.tensor(x_nor, dtype=torch.float32)
y_nor = torch.tensor(y_nor, dtype=torch.float32)
y_tensor = y_nor.view(100,1)

criterion = torch.nn.MSELoss() # Defined loss function
optimizer = torch.optim.SGD(model.parameters(), lr=0.01) # Defined optimizer
```


```python
n_bitch = 10

for epoch in range(1000):
    # Forward pass
    #print(epoch)
    #print(n_bitch)
    #x_train_bitch = x_set[epoch*n_bitch : epoch*n_bitch+n_bitch]
    #y_train_bitch = y_set[epoch*n_bitch : epoch*n_bitch+n_bitch]

    y_pred = model(x_tensor)
    #print(y_pred)
    #print("---------------------")
    #print(y_tensor)
    # Compute loss
    loss = criterion(y_pred, y_tensor)
    #print(epoch, loss)

    # Zero gradients
    optimizer.zero_grad()
    # perform backward pass
    loss.backward()
    # update weights
    optimizer.step()

x = np.linspace(0,1,10)
y = x*model.linear.weight.detach().numpy()[0]+model.linear.bias.detach().numpy()[0]
plt.plot(x,y)
plt.scatter(x_nor,y_nor)
plt.show()
```
