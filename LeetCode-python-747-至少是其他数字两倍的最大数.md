 [题目链接](https://leetcode-cn.com/problems/largest-number-at-least-twice-of-others/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 在一个给定的数组nums中，总是存在一个最大元素 。

查找数组中的最大元素是否至少是数组中每个其他数字的两倍。

如果是，则返回最大元素的索引，否则返回-1。
 
**示例1**
> 输入: nums = [3, 6, 1, 0]
输出: 1
解释: 6是最大的整数, 对于数组中的其他整数,
6大于数组中其他元素的两倍。6的索引是1, 所以我们返回1.

**示例2**
>输入: nums = [1, 2, 3, 4]
输出: -1
解释: 4没有超过3的两倍大, 所以我们返回 -1.

#### 解题思路
***
 找最大的数和第二大的数，看是否最大的数是第二大数的两倍

#### 代码实现
```python
class Solution(object):
    def dominantIndex(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        if n==1:
            return 0
        stack= [0,1] if nums[1]> nums[0] else [1,0]    
        for i in range(2, n):
            if nums[i] > nums[stack[1]]:
                stack = stack[1:]+[i]
            elif nums[i] > nums[stack[0]]:
                stack = [i] + stack[1:]     
        return stack[1] if nums[stack[1]] >=nums[stack[0]]*2 else -1
```

本文链接：[https://www.jianshu.com/p/9bbf7f3d2bd6](https://www.jianshu.com/p/9bbf7f3d2bd6)
