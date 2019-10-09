 [题目链接](https://leetcode-cn.com/problems/bitwise-and-of-numbers-range/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 给定范围 [m, n]，其中 0 <= m <= n <= 2147483647，返回此范围内所有数字的按位与（包含 m, n 两端点）。

 
**示例1**
> 输入: [5,7]
输出: 4

**示例2**
> 输入: [0,1]
输出: 0

#### 解题思路
***
 当n的二进制形式长度大于m的二进制形式的长度时，直接返回0
否则$2^k<=m<n<2^{k+1}$时，需要找到m和n的最长相同的前缀，n从后往前消1,直到小于m



#### 代码实现
```python
class Solution(object):
    def rangeBitwiseAnd(self, m, n):
        """
        :type m: int
        :type n: int
        :rtype: int
        """
        while m<n:
            n = n & (n-1)
        return n
```

本文链接：[https://www.jianshu.com/p/e8bff9bd4e65](https://www.jianshu.com/p/e8bff9bd4e65)
