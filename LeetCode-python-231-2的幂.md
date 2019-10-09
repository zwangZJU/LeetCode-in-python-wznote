 [题目链接](https://leetcode-cn.com/problems/power-of-two/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学
***
 给定一个整数，编写一个函数来判断它是否是 2 的幂次方。

**示例**
> 输入: 1
输出: true
解释: 20 = 1

**示例2**
> 输入: 16
输出: true
解释: 24 = 16

**示例3**
> 输入: 218
输出: false


#### 解题思路
***
若n为 2的幂，则n的二进制表示中只有一个1在最高为，n-1的二进制全都是1，且比n的二进制少一位
则 n&(n-1)为0




#### 代码实现
```
class Solution(object):
    def isPowerOfTwo(self, n):
        """
        :type n: int
        :rtype: bool
        """
        if n<=0:
            return False
        return not n&(n-1)
```

本文链接：[https://www.jianshu.com/p/fb710983902c](https://www.jianshu.com/p/fb710983902c)
