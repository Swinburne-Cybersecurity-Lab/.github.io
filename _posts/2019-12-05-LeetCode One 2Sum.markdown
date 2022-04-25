---
layout:     post
title:      "LeetCode One 2Sum"
subtitle:   " \"Algorithm\""
date:       2019-12-05 16:58:00
author:     "Nastul"
header-img: "img/c62118211cf7422e8534e259f2f92e5e.jpeg"
tags:
    - LeetCode 
---
**Two Sum**

蛮力求解：

遍历所有的变量的和，得到target

Time:
$$
O(n^{2})
$$
Space:
$$
O(1)
$$


```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)):
            for j in range(i+1,len(nums)):
                if nums[i]+nums[j]==target:
                    return [i,j]
```
利用字典：

Time:
$$
O(n)
$$
Space:
$$
O(n)
$$


```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dic = dict()
        for i in range(len(nums)):
            if (target-nums[i])  in  dic.keys()  :
                return [i, dic[target-nums[i]]]
            else:
                dic[nums[i]] = i
```


**Two Sum II - Input array is sorted**

由于数组是排序的，所以蛮力很容易Time out,  字典的方法是可行的。 另一种方法是从列表的两头向中间逼近。

```python
class Solution :
	def twoSum(self, numbers: List[int], target: int) -> List[int]:
        l = 0
        r = len(numbers)- 1
        while (numbers[l] + numbers[r] != target):
            if (numbers[l] + numbers[r] > target):
                r-=1;
            else :
                l+=1;        
        return [l + 1, r + 1];
```
**Two Sum III - Data structure design**

Design and implement a TwoSum class. It should support the following operations: add and find.

add - Add the number to an internal data structure.
find - Find if there exists any pair of numbers which sum is equal to the value.









**Two Sum IV - Input is a BST**

第一个方法先将bst中序遍历转成list。 然后和上面的方法一样进行搜索

```python

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
    def tree_to_list_in(self,root):
       if root.left==None and root.right==None:
        return [root.val]
    
        elif root.left==None:
            return  [root.val] + self.tree_to_list_in(root.right)
        elif root.right==None:
            return  self.tree_to_list_in(root.left)+[root.val]
    	return self.tree_to_list_in(root.left)+ [root.val] + self.tree_to_list_in(root.right)
```


​    
```python
def findTarget(self, root: TreeNode, k: int) -> bool:
    tree_list = self.tree_to_list_in(root)
    l = 0
    r = len(tree_list)- 1
    while (tree_list[l] + tree_list[r] != k and l < r):
        if (tree_list[l] + tree_list[r] > k):
            r-=1;
        else :
            l+=1;   
    if r <= l:
        return False
    else:
        return True;
```