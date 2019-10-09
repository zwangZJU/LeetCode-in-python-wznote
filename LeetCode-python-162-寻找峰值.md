 [题目链接](https://leetcode-cn.com/problems/find-peak-element/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 峰值元素是指其值大于左右相邻值的元素。

给定一个输入数组 nums，其中 nums[i] ≠ nums[i+1]，找到峰值元素并返回其索引。

数组可能包含多个峰值，在这种情况下，返回任何一个峰值所在位置即可。

你可以假设 nums[-1] = nums[n] = -∞。
 

 
**示例1**
> 输入: nums = [1,2,3,1]
输出: 2
解释: 3 是峰值元素，你的函数应该返回其索引 2。

**示例2**
> 输入: nums = [1,2,1,3,5,6,4]
输出: 1 或 5 
解释: 你的函数可以返回索引 1，其峰值元素为 2；
     或者返回索引 5， 其峰值元素为 6。
 
#### 解题思路
***
 二分法
左指针移动的条件是nums[mid]<nums[mid+1]
反之，右指针移动



#### 代码实现
```
class Solution(object):
    def findPeakElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        left = 0
        right = len(nums)-1
        while left<right:
            mid = (left+right)//2
            if nums[mid]<nums[mid+1]:
                left = mid+1
            else:
                right = mid
        return left
```

本文链接：[https://www.jianshu.com/p/3e2efbf8e86c](https://www.jianshu.com/p/3e2efbf8e86c)
