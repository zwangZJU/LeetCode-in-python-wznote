 [题目链接](https://leetcode-cn.com/problems/sqrtx/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学
***
 实现 int sqrt(int x) 函数。

计算并返回 x 的平方根，其中 x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。
 
**示例1**
> 输入: 4
输出: 2

**示例2**
> 输入: 8
输出: 2
说明: 8 的平方根是 2.82842..., 由于返回类型是整数，小数部分将被舍去。

#### 解题思路
***
牛顿迭代:
问题为$x^2 = y$，其中$y$是常数，$x$是未知数，将其改写为习惯的数学形式：
$$f(x)=x^2-y$$
目标就变成了找到一个$x$使$f(x)=0$
自然想到了牛顿迭代法：
把$f(x)$在某一点$x_0$的邻域内展开成泰勒级数，取其线性部分，并令其等于0：
$$f(x)=f(x_0)+f'(x_0)(x-x_0)=0$$
得到迭代关系式：
$$x_{n+1}=x_n-\frac{f(x_n)}{f'(x_n)}$$
因为不用求精确解，所以迭代到$x^2$不大于$y$时停止即可

初值$x_0$可以设置为$y$



#### 代码实现
```python
class Solution:
    def mySqrt(self, x):
        """
        :type x: int
        :rtype: int
        """
        r = x
        while r*r > x:
            r = int((r + x/r) / 2)
        return r
```
本文链接：[https://www.jianshu.com/p/e6dd97bbcd40](https://www.jianshu.com/p/e6dd97bbcd40)

 
