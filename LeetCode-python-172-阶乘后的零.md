 [题目链接](https://leetcode-cn.com/problems/factorial-trailing-zeroes/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学
***
 给定一个整数 n，返回 n! 结果尾数中零的数量。

 
**示例1**
> 输入: 3
输出: 0
解释: 3! = 6, 尾数中没有零。

**示例1**
>输入: 5
输出: 1
解释: 5! = 120, 尾数中有 1 个零.

#### 解题思路
***
 只有5*2可以得到0
只要有偶数就能分解出2，2的个数一定比5多，所以只用计算5的个数
对于20来说，只有5，10，15，20包含5，故20!结尾有20/5=4个零
当然不止这么简单，对于25来说：只有5，10，15，20，25，包含5，结尾却有6个零，因为25=5x5，包含两个5
所以f(n)=n/5+f(n/5)

#### 代码实现
```python
class Solution(object):
    def trailingZeroes(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n<5:
            return 0
        if n<10:
            return 1
        return n/5 + self.trailingZeroes(n/5)
```
本文链接：[https://www.jianshu.com/p/2a1415790a58](https://www.jianshu.com/p/2a1415790a58)

 
