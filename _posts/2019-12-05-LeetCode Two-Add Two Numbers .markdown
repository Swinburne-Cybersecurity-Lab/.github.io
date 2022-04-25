---
layout:     post
title:      "LeetCode Two-Add Two Numbers"
subtitle:   " \"Algorithm\""
date:       2019-12-05 19:59:00
author:     "Nastul"
header-img: "img/c62118211cf7422e8534e259f2f92e5e.jpeg"
tags:
    - LeetCode 
---
**Add Two Numbers**

两个链表求和

构造链表

```python
class ListNode:
    def __init__(self, x):
        self.val = x
        self.next = None
```
```python
#实例化链表
node = ListNode(2)
tail = node
tail.next = ListNode(4)
tail=tail.next
```

```python
#这里的主要问题是[1]  [9,9] 的时候要考虑到，进位两次的问题
def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
    newListNode = ListNode(0)
    tail = newListNode
    next_number = 0
    while l1 !=None or l2 != None or next_number!=0:
        val1=0
        val2=0
        if l1:
            val1=l1.val
            l1=l1.next
        if l2:
            val2=l2.val
            l2=l2.next  
        now_number = (val1+val2+next_number)%10
        next_number = (val1+val2+next_number)//10
        tail.val =  now_number
        tail.next = None        
        if next_number == 0 and not l1 and not l2 :
            break
        tail.next = ListNode(next_number)
        tail = tail.next
    return newListNode
```
**Add Two Numbers II**

这里假设链表存得数是从高位到低位的

ps: 不可以反转链表

首先想到的是用栈去做，就可以当作第一个问题来做了

```python
def addTwoNumbers(self, l1: ListNode, l2: ListNode) -> ListNode:
    stack1 = []
    stack2 = []
    stack3 = []
    while l1!=None or l2!= None:
        
        if l1:
            stack1.append(l1.val)
            l1=l1.next
        if l2:
            stack2.append(l2.val)
            l2=l2.next
    
    next_number = 0
    while stack1 or stack2 or next_number!=0:
        val1=0
        val2=0
        if stack1:
            val1 = stack1.pop()
        if stack2:
            val2 = stack2.pop()  
        print(val1)
        now_number = (val1+val2+next_number)%10
        next_number = (val1+val2+next_number)//10            
        stack3.append (now_number)

        if next_number == 0 and not stack1 and not stack2 :
            break
    newListNode = ListNode(stack3.pop())
    tail = newListNode
    
    while stack3:
        tail.next =  ListNode(stack3.pop())
        tail = tail.next
        
    return newListNode
```
**Reverse Linked List**

也是通过栈来做



**Reverse Linked List II**

只反转给定了 m,n 中间的数字， 通过栈记录中间位置的数



