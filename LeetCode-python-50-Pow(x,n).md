 [题目链接](https://leetcode-cn.com/problems/powx-n/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  递归
***
实现 [pow(*x*, *n*)](https://www.cplusplus.com/reference/valarray/pow/) ，即计算 x 的 n 次幂函数。 

**示例1**
> 输入: 2.00000, 10
输出: 1024.00000

**示例2**
> 输入: 2.10000, 3
输出: 9.26100

**示例3**
> 输入: 2.00000, -2
输出: 0.25000
解释: 2-2 = 1/22 = 1/4 = 0.25

#### 解题思路
***
 三种情况：
n%2=0：如$3^{50} = 3^{25} \times 3^{25}$
n%2=1: 如$3^{25}=3^{12} \times 3^{12} \times 3$
n<0:如$2^{-3}=(\frac{1}{2})^{3}$



#### 代码实现
```python
class Solution(object):
    def myPow(self, x, n):
        """
        :type x: float
        :type n: int
        :rtype: float
        """
        if n==0: return 1
        if n<0:
            return self.myPow(1/x, -n)
        half = self.myPow(x, n/2)
        if n%2 == 0:
            return half*half
        if n>0:
            return half*half*x
```

本文链接：[https://www.jianshu.com/p/09b572f4adc4](https://www.jianshu.com/p/09b572f4adc4)
