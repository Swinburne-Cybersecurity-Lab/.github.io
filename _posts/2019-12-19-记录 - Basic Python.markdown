---
layout:     post
title:      "记录 - Basic Python"
subtitle:   " \"Traditional NLP\""
date:       2019-12-19 00:11:00
author:     "Nastul"
header-img: "img/prml1.jpg"
tags:
    - Python
---
> ```python
> #!/usr/bin/env python3
> # -*- coding: utf-8 -*-
> ```



虽然代码最近两年一直都用的python， 但是都是现查文档，现写，所以记录下基本的东西在这里

input() 读取输入的str

***

**Python 中的基本数据类型：**

Number, 数字类型，包括了 整数 （int,hex,bin)  浮点数(float, double 这里有个科学计数法e 代表10, 浮点数也有精度的问题)    

String,字符串类型，  ord()字符串整数表示， chr() 转为字符   str(), 如果需要传输，就需要将str变成字节为单位的bytes, 在 b"string"

> encode() 可以编码string为指定的bytes. eg. 'string'.encode('asscii) decode()相反的操作
>
> 在`bytes`中，无法显示为ASCII字符的字节，用`\x##`显示。

Bool类型， 计算中有 and or not 

None值  

Var   动态类型语言，变量的类型不需要固定。 赋值给变量的时候只是将变量指向了目标的地址

常量通常用大写表示。

> Tips: Python的整数没有大小限制，浮点数也没有大小限制，但是超出一定范围就直接表示为`inf`

字符编码问题： ASCII 127,     GBK ，  但是全世界的编码就会出现冲突，所以出现了万国码Unicode 通常用两个字节表示一个字符，也有可能是4个字节，但是如果全都是英文就会十分的浪费空间，于是出现了UTF-8 可变长编码，所以计算机中可以使用unicode， 需要传输或者保存使用utf-8  

在python3中使用 unicode编码。



**格式化**

占位符: %d,%f,%s,%x.  %可以转义自己.

```python
"this %s a test %d" % ("is",2)
#{0} {1} 来表示占位。 {0:.1f}可以表示需要精确的位数, 四舍五入
"this {0} a test {1}".format("is",2)
```

**List,Tuple,Set,Dict**

List: append(), insert(),pop(i),

Tuple: 一旦初始化就不能修改。 只是保证指向的对象不变，但是对象所指向的内容是可以改变的

Dict:可以通过get方法获取指定的值 d.get('str',-1) 不指定返回值返回None. key值一定要是不可变对象

Set: add()可以添加元素。 & 交集    | 并集

**函数**

pass作为函数的占位符

isinstance(x, (int,float)) 判断x类型

必选参数在前，默认参数在后。 默认参数必须指向不变对象， 不会出错，但是结果不对。

def fun(*number) 可变参数

```
#命名关键字参数
def person(name, age, *, city, job):
#如果函数定义中已经有了一个可变参数，后面跟着的命名关键字参数就不再需要一个特殊分隔符*了
def person(name, age, *args, city, job):

```

def fun(*args,**kwargs):  

位置参数 args 可变参数，关键词参数kwargs

递归优化:尾递归。

> 尾递归是指，在函数返回的时候，调用自身本身，并且，return语句不能包含表达式。这样，编译器或者解释器就可以把尾递归做优化，使递归本身无论调用多少次，都只占用一个栈帧，不会出现栈溢出的情况。
>

python 依然会存在爆栈的问题

切片[::]

只要是可迭代对象就可以使用迭代。

> for k, v in d.items()
>
> ```python
> >>> from collections import Iterable
> >>> isinstance('abc', Iterable) # str是否可迭代
> #将迭代对象变成有索引
> for i, value in enumerate(['A', 'B', 'C'])
> ```

**列表生成式**

```python
[x * x for x in range(1, 11) if x % 2 == 0]
[m + n for m in 'ABC' for n in 'XYZ']
```

**生成器**

> 所以，如果列表元素可以按照某种算法推算出来，那我们是否可以在循环的过程中不断推算出后续的元素呢？这样就不必创建完整的list，从而节省大量的空间。在Python中，这种一边循环一边计算的机制，称为生成器：generator。

只要把一个列表生成式的`[]`改成`()`

要把`fib`函数变成generator，只需要把`print(b)`改为**`yield b`**就可以了  

这就是定义generator的另一种方法。如果一个函数定义中包含`yield`关键字，那么这个函数就不再是一个普通函数，而是一个generator：

> ```python
> #这里需要捕获错误
> >>> g = fib(6)
> >>> while True:
> ...     try:
> ...         x = next(g)
> ...         print('g:', x)
> ...     except StopIteration as e:
> ...         print('Generator return value:', e.value)
> ...         break
> ```

生成器都是 Iterator， 但是list dict str 是可迭代的却不是Iterator。  iter( ) 可以将他们变成Iterator

> 为什么`list`、`dict`、`str`等数据类型不是`Iterator`？
>
> 这是因为Python的`Iterator`对象表示的是一个数据流，Iterator对象可以被`next()`函数调用并不断返回下一个数据，直到没有数据时抛出`StopIteration`错误。可以把这个数据流看做是一个有序序列，但我们却不能提前知道序列的长度，只能不断通过`next()`函数实现按需计算下一个数据，所以`Iterator`的计算是惰性的，只有在需要返回下一个数据时它才会计算。
>
> `Iterator`甚至可以表示一个无限大的数据流，例如全体自然数。而使用list是永远不可能存储全体自然数的。

**内置函数**

变量可以指向函数

map/reduce

map(func,[]) func  接收一个参数

reduce(fuc,[])  fuc 接收两个参数，把结果继续和序列的下一个元素做累积计算

filter(func,[]) fuc返回bool

> 计算[素数](http://baike.baidu.com/view/10626.htm)的一个方法是[埃氏筛法](http://baike.baidu.com/view/3784258.htm)
>
>  返回闭包时牢记一点：返回函数不要引用任何循环变量，或者后续会发生变化的变量。

**装饰器**Decorator :在代码运行期间动态增加功能的方式

> ```python
> def log(func):
>     def wrapper(*args, **kw):
>         print('call %s():' % func.__name__)
>         return func(*args, **kw)
>     return wrapper
> #把@log放到now()函数的定义处，相当于执行了语句： now = log(now)
> @log
> def now():
>     print('2015-3-25')
> ```

**偏函数**

> `functools.partial`的作用就是，把一个函数的某些参数给固定住（也就是设置默认值），返回一个新的函数，调用这个新函数会更简单。
>
> ```python
> int2 = functools.partial(int, base=2)
> ```



**模块**

每一个包目录下面都会有一个`__init__.py`

任何模块代码的第一个字符串都被视为模块的文档注释

```python
#可以保证当前模块代码作为主程序运行时执行的代码，但是被import的时候不运行
if __name__=='__main__':
    test()
#这样的变量不应该被直接引用
_abc
```

**OOP**

> ```python
> #定义
> def __init__(self, name, score)：
> #如果要让内部属性不被外部访问， 属性名称前加上两个下划线__
> #前后有都两个下划线的时候是特殊变量，是可以直接访问的
> ```

动态给类绑定属性 class.func=func

> Python允许在定义class的时候，定义一个特殊的`__slots__`变量，来限制该class实例能添加的属性：
>
> `__slots__`定义的属性仅对当前类实例起作用，对继承的子类是不起作用的：
>
> ```python
> class Student(object):
>     __slots__ = ('name', 'age') # 用tuple定义允许绑定的属性名称
>     
>     
> @property
> 
> @score.setter
> 
> 
> 多重继承 ManIn
> ```

**调试**

> ```python
> #-o 可以关闭
> assert n != 0, 'n is zero!'
> 
> import logging
> logging.basicConfig(level=logging.INFO)
> logging.info('')
> ```

**序列化**

```python
import pickle
d = dict(name='Bob', age=20, score=88)
pickle.dumps(d,f)
d = pickle.load(f)

json dump
```

**进程线程**

```python
#子进程永远返回0，而父进程返回子进程的ID。这样做的理由是，一个父进程可以fork出很多子进程，所以，父进程要记下每个子进程的ID，而子进程只需要调用getppid()就可以拿到父进程的ID。
pid = os.fork()


#from multiprocessing import Process
#跨平台解决方案
from multiprocessing import Process
import os

# 子进程要执行的代码
def run_proc(name):
    print('Run child process %s (%s)...' % (name, os.getpid()))

if __name__=='__main__':
    print('Parent process %s.' % os.getpid())
    p = Process(target=run_proc, args=('test',))
    print('Child process will start.')
    p.start()
    p.join()
    print('Child process end.')
#创建子进程时，只需要传入一个执行函数和函数的参数，创建一个Process实例，用start()方法启动，这样创建进程比fork()还要简单。join()方法可以等待子进程结束后再继续往下运行，通常用于进程间的同步。

#进程池
from multiprocessing import Pool
import os, time, random

def long_time_task(name):
    print('Run task %s (%s)...' % (name, os.getpid()))
    start = time.time()
    time.sleep(random.random() * 3)
    end = time.time()
    print('Task %s runs %0.2f seconds.' % (name, (end - start)))

if __name__=='__main__':
    print('Parent process %s.' % os.getpid())
    p = Pool(4)
    for i in range(5):
        p.apply_async(long_time_task, args=(i,))
    print('Waiting for all subprocesses done...')
    p.close()
    p.join()
    print('All subprocesses done.')
    
#进程间通信，消息队列
#线程
t = threading.Thread(target=loop, name='LoopThread')
t.start()
t.join()

#Lock
lock = threading.Lock()
        lock.acquire()
            lock.release()

#ThreadLocal
local_school = threading.local()
    # 获取当前线程关联的student:
    std = local_school.student
    
#全局变量local_school就是一个ThreadLocal对象，每个Thread对它都可以读写student属性，但互不影响。你可以把local_school看成全局变量，但每个属性如local_school.student都是线程的局部变量，可以任意读写而互不干扰，也不用管理锁的问题，ThreadLocal内部会处理    
```

**正则表达式**

re模块

**时间**

```python
from datetime import datetime,timedelta
now = datetime.now()
cday = datetime.strptime('2015-6-1 18:19:59', '%Y-%m-%d %H:%M:%S')
#返回时间差
timedelta.total_seconds()
```



**网络部分**

```python
# 导入socket库:
import socket
# 创建一个socket:AF_INET指定使用IPv4协议
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
# 建立连接:
s.connect(('www.sina.com.cn', 80))

# 监听端口:
s.bind(('127.0.0.1', 9999))
s.listen(5)
```

