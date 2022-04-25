---
layout:     post
title:      "LeetCode Three-子串问题"
subtitle:   " \"Algorithm\""
date:       2020-04-08 08:18:00
author:     "Nastul"
header-img: "img/c62118211cf7422e8534e259f2f92e5e.jpeg"
tags:
    - LeetCode 
---
**[最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/)**

特殊情况  abba也是，所以不能只考虑奇数个数的字符



**爆破**

找到字符串中所有大于等于2的子串，然后判断该子串是否是回文子串



**动规**

画一张表，横竖分别是需要判断的字符串，当s[l]==s[r]而且dp[l+1]==dp[r-1]的时候将dp[l] [r]赋值为True , 也就是判断左右字符串是否相等，判断左右字符串的前一个是否相等。



**中心扩撒**

直接从中间开始找回文，注意回文子串的奇偶

```python
    def longestPalindrome(self, s: str) -> str:

        new_list = []
        new_list.append("#")
        for i in s:
            new_list.append(i)
            new_list.append("#")

        max_str=(0,0)
        max_len = 0
        for i in range(len(new_list)):
            left=i
            right=i

            while left>=0 and right <=len(new_list)-1 :
                if new_list[left]==new_list[right]:
                    if left>0 and right <len(new_list)-1:
                        left-=1
                        right+=1
                    else:
                        break
                else:
                    left+=1
                    right-=1
                    break

            sub_len = right-left
            if sub_len > max_len:
                max_str = (left//2,right//2)
                max_len = sub_len

        return s[max_str[0]:max_str[1]]
```





**马拉车**

字串的间隙加上#，包括首尾





**[无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)**

滑动窗口

i 从左往右依次遍历， j 从i+1处遍历，直到重复 i+1  j 从重复处遍历

一个数组就可以解决，将不重复的元素存入list中，遇到重复的元素就找到重复的位置，从后一位截取到最后继续遍历





**[有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)**

栈





#### **[整数反转](https://leetcode-cn.com/problems/reverse-integer/)**

从低位一位一位的取出， %10

判断是否溢出， boundry = (1<<31) -1 if x>0 else 1<<31

```python
#效率不高
class Solution:
    def reverse(self, x: int) -> int:
        rev = 0
        sym = False
        if x < 0 :
            sym = True
        x = abs(x)
        while x > 0:
            single = x % 10
            x = x // 10

            if rev > 2147483647/10:
                return 0

            rev = rev*10 + single
        if sym:
            return -rev
        else:
            return rev
```

(a & b)
按位与运算符：参与运算的两个值,如果两个相应位都为1,则该位的结果为1,否则为0
输出结果 12 ，二进制解释： 0000 1100

(a | b)
按位或运算符：只要对应的二个二进位有一个为1时，结果位就为1。
输出结果 61 ，二进制解释： 0011 1101

(a ^ b)
按位异或运算符：当两对应的二进位相异时，结果为1
输出结果 49 ，二进制解释： 0011 0001

(~a )
按位取反运算符：对数据的每个二进制位取反,即把1变为0,把0变为1 。~x 类似于 -x-1
输出结果 -61 ，二进制解释： 1100 0011，在一个有符号二进制数的补码形式。

a << 2
左移动运算符：运算数的各二进位全部左移若干位，由 << 右边的数字指定了移动的位数，高位丢弃，低位补0。
输出结果 240 ，二进制解释： 1111 0000

a >> 2
右移动运算符：把">>"左边的运算数的各二进位全部右移若干位，>> 右边的数字指定了移动的位数
输出结果 15 ，二进制解释： 0000 1111





**[最大正方形](https://leetcode-cn.com/problems/maximal-square/)**

动规，左，上，斜上方的最小值+1 来更新当前值

[0]*n 初始化  n m 维度的dp数组



#### [最长有效括号](https://leetcode-cn.com/problems/longest-valid-parentheses/)

利用栈来解决，初始时候-1 入栈，考虑一开始（） 的情况可以计算出正确的位置，（ 入栈    ）如有匹配的就  （弹栈， 位置减去栈顶元素， 如果栈为空就把）位置入栈



```python
class Solution:
    def longestValidParentheses(self, s: str) -> int:
        max_length = 0
        sub_length = 0
        stack = []
        stack.append(-1)
        for i, item in enumerate(s):
            if item =="(":
                stack.append(i)
            else:
                stack.pop()
                if stack==[]:
                    stack.append(i)
                else:
                    sub_length = i - stack[-1]
            if sub_length > max_length:
                max_length = sub_length

        return max_length
```





#### [字符串相乘](https://leetcode-cn.com/problems/multiply-strings/)

效率比较低的解法，每一位分别相乘相加

```python
class Solution(object):
    def multiply(self, num1, num2):
        """
        :type num1: str
        :type num2: str
        :rtype: str
        """
        len_num1 = len(num1)
        len_num2 = len(num2)
        temp = 0
        for i,number_i in  enumerate(num1) :
            for j,number_j in enumerate(num2) :
                temp =temp + pow(10,len_num1-1-i)* int(number_i) * pow(10,len_num2-1-j)* int(number_j)
        return str(temp)
```





#### [字符串解码](https://leetcode-cn.com/problems/decode-string/)

主要问题是[]的嵌套问题，用栈来解决，遇到[入栈  ]出栈，  栈里存放之前的字符串和之后字符串需要重复的次数

```python
class Solution:
    def decodeString(s: str) -> str:
        stack_data = []
        number = 0
        string = ''
        for i in s:
            print(i)
            print("stack_data:",stack_data)
            #如果i是数组的话，就存入number中
            if i.isdigit():
                #有多位的情况需要进位
                number = number * 10 + int(i)
            #如果i是字符串，那就存到string中
            elif i.isalpha():
                string += i
            #遇到[ 数据入栈，清空临时变量
            elif i == '[':
                #保存之前的string
                stack_data.append((string,number))
                number = 0
                string = ''
            elif i == ']': 
                #这里拿出来之前的字符串，然后和当前的字符串拼接
                final_str, final_number = stack_data.pop()
                print("string:",string)
                string = final_str + final_number * string
        return string
```

