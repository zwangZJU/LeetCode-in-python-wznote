 [题目链接](https://leetcode-cn.com/problems/ugly-number-ii/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学、数组
***
 编写一个程序，找出第 n 个丑数。

丑数就是只包含质因数 2, 3, 5 的正整数。

 
**示例**
> 输入: n = 10
输出: 12
解释: 1, 2, 3, 4, 5, 6, 8, 9, 10, 12 是前 10 个丑数。
#### 解题思路
***
从小到大依次计算出第i个丑数，知道第n个为止
丑数的计算方法：
已有的丑数分别乘以2，3，5后得到的值中最小的那一个



#### 代码实现
```
class Solution(object):
    def nthUglyNumber(self, n):
        """
        :type n: int
        :rtype: int
        """
        ugly = [1]
        i2, i3, i5 = 0, 0, 0
        while n > 1:
            u2, u3, u5 = 2 * ugly[i2], 3 * ugly[i3], 5 * ugly[i5]
            umin = min((u2, u3, u5))
            if umin == u2:
                i2 += 1
            if umin == u3:
                i3 += 1
            if umin == u5:
                i5 += 1
            ugly.append(umin)
            n -= 1
        return ugly[-1]
```

本文链接：[https://www.jianshu.com/p/f5d01459e5be](https://www.jianshu.com/p/f5d01459e5be)
