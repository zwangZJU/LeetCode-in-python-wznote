 [题目链接](https://leetcode-cn.com/problems/missing-number/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、数学
***
 给定一个包含 0, 1, 2, ..., n 中 n 个数的序列，找出 0 .. n 中没有出现在序列中的那个数。

 
**示例1**
> 输入: [3,0,1]
输出: 2

**示例2**
>输入: [9,6,4,2,3,5,7,0,1]
输出: 8

#### 解题思路
***
方法1：
 1到n的和是$\frac{n*(n-1)}{2}$，数组长度为n时，是0到n+1的数列中缺失了一个数，用该有的和-当前数组元素的和=缺失的数字

方法2：
数组中所有的数字与1到n+1进行异或操作，出现两次的数都会消失，只剩下出现一次的数，即为缺失的数
类似于[136.只出现一次的数字](https://www.jianshu.com/p/f3c2a20da915)



#### 代码实现
方法1：
```python
class Solution:
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        return  n*(n+1)//2 - sum(nums) 
```
方法2：
```python
class Solution:
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        res = 0
        for i, num in enumerate(nums):
            res ^= (i+1) ^ num
        return res
```

本文链接：[https://www.jianshu.com/p/3dd5fa2996a6](https://www.jianshu.com/p/3dd5fa2996a6)
