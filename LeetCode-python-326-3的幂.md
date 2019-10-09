 [题目链接](https://leetcode-cn.com/problems/power-of-three/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学
***
给定一个整数，写一个函数来判断它是否是 3 的幂次方。
 
**示例1**
> 输入: 27
输出: true

**示例2**
> 输入: 0
输出: false

**示例3**
> 输入: 9
输出: true

**示例4**
> 输入: 45
输出: false

#### 解题思路
***
 当能被3整除时一直除以三，最终能到1，就是3的幂

或者
n>0且最大的3的幂能整除n



#### 代码实现
方法1：
```python
class Solution(object):
    def isPowerOfThree(self, n):
        """
        :type n: int
        :rtype: bool
        """
        if n > 0:
            while n%3 == 0:
                n /= 3
        return n == 1
```

方法2：
```python
class Solution(object):
    def isPowerOfThree(self, n):
        return n > 0 and 1162261467 % n == 0
```
本文链接：[https://www.jianshu.com/p/ed86cad472f0](https://www.jianshu.com/p/ed86cad472f0)
