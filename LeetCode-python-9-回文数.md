 [题目链接](https://leetcode-cn.com/problems/palindrome-number/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学
***
 判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

 
**示例1**
> 输入: 121
输出: true

**示例2**
>输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。 

**示例3**
>输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。

#### 解题思路
***
 int转成str，比较正序和逆序的字符串是否一样



#### 代码实现
```
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        x = str(x)
        return x == x[::-1]
```

本文链接：[https://www.jianshu.com/p/fcda7fe9dfdc](https://www.jianshu.com/p/fcda7fe9dfdc)
