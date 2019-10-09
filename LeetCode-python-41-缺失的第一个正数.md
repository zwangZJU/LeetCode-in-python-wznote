 [题目链接](https://leetcode-cn.com/problems/first-missing-positive/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、桶排序
***
 给定一个未排序的整数数组，找出其中没有出现的最小的正整数。

 
**示例1**
> 输入: [1,2,0]
输出: 3

**示例2**
>输入: [3,4,-1,1]
输出: 2

**示例3**
>输入: [7,8,9,11,12]
输出: 1

#### 解题思路
***
 长度为n的数组，缺失的第一个正数一定为1到n+1之间的一个数

初始化一个值全为True的长度为n的桶
遍历数组，遇到大于n或小于1的数不管，遇到其余的数在桶中相应的位置设为False
遍历完数组后遍历桶，第一个为True的桶的下标就是缺失的第一个正数
若全为False,就返回n+1

#### 代码实现
```python
class Solution(object):
    def firstMissingPositive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if 1 not in nums:
            return 1
        n = len(nums)
        bucket = [True]*(n+1)
        for i in range(n):
            if 0<nums[i]<=n:
                bucket[nums[i]] = False
        for i in range(1,n+1):
            if bucket[i]:
                return i
        return n+1
```

本文链接：[https://www.jianshu.com/p/818a96141e74](https://www.jianshu.com/p/818a96141e74)
