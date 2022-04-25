---
layout:     post
title:      "LeetCode Three-跳跃问题"
subtitle:   " \"Algorithm\""
date:       2020-04-08 08:18:00
author:     "Nastul"
header-img: "img/c62118211cf7422e8534e259f2f92e5e.jpeg"
tags:
    - LeetCode 
---
**[跳跃游戏 II](https://leetcode-cn.com/problems/jump-game-ii/)**

特殊情况  abba也是，所以不能只考虑奇数个数的字符



**爆破**

找到字符串中所有大于等于2的子串，然后判断该子串是否是回文子串



**动规**

画一张表，横竖分别是需要判断的字符串，当s[l]==s[r]而且dp[l+1]==dp[r-1]的时候将dp[l] [r]赋值为True , 也就是判断左右字符串是否相等，判断左右字符串的前一个是否相等。



**中心扩撒**

直接从中间开始找回文，注意回文子串的奇偶



**马拉车**

字串的间隙加上#，包括首尾





**[无重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)**

滑动窗口

i 从左往右依次遍历， j 从i+1处遍历，直到重复





**[有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)**

栈





#### **[整数反转](https://leetcode-cn.com/problems/reverse-integer/)**

从低位一位一位的取出， %10

判断是否溢出， boundry = (1<<31) -1 if x>0 else 1<<31



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

找到当前位置能跳的最大距离，其中所有的位置都可以作为下一个起跳点，依次遍历起跳点找到最远的位置。



```python
class Solution:
    def jump(self, nums: List[int]) -> int:
        """
        :type nums: List[int]
        :rtype: int
        """
        jump_number = 0
        index = 0
        while index < len(nums)-1:
            

            can_jumpnum = nums[index]
            if (index+can_jumpnum) >= len(nums)-1:
                return jump_number+1
            temp_index = index+can_jumpnum+1
            max_index = 0
            max_number = 0
            for i, number  in enumerate(nums[index+1:temp_index]):

                if max_number < (i+number+1):
                    max_number = i+number+1
                    max_index = i+1

            jump_number+=1
            index+=max_index

        return jump_number
```

