[题目链接](https://leetcode-cn.com/problems/ugly-number/submissions/)
难度： 简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数学
***
编写一个程序判断给定的数是否为丑数。

丑数就是只包含质因数 2, 3, 5 的正整数。

**示例1**
>输入: 6
输出: true
解释: 6 = 2 × 3

**示例2**
>输入: 8
输出: true
解释: 8 = 2 × 2 × 2
示例 3:

**示例3**
>输入: 14
输出: false 
解释: 14 不是丑数，因为它包含了另外一个质因数 7。

####解题思路
让num依次除以2，3，5直到不能整除为止，若此时为1，说明是丑数

#### 代码实现
```
class Solution(object):
    def isUgly(self, num):
        """
        :type num: int
        :rtype: bool
        """
        if num<=0:
            return False
        for i in [2, 3, 5]:
            while num % i == 0:
                num /= i
        return num == 1
```

本文链接：[https://www.jianshu.com/p/bc30b640c9c4](https://www.jianshu.com/p/bc30b640c9c4)
