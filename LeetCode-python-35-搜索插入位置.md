 [题目链接](https://leetcode-cn.com/search-insert-position/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、二分查找
***
 给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

你可以假设数组中无重复元素。

 
**示例1**
> 输入: [1,3,5,6], 5
输出: 2
 
**示例2**
> 输入: [1,3,5,6], 2
输出: 1

**示例3**
> 输入: [1,3,5,6], 7
输出: 4

**示例4**
> 输入: [1,3,5,6], 0
输出: 0

#### 解题思路
***
普通的二分查找，找到了就返回索引，找不到就返回搜索到最后指针停留的位置



#### 代码实现
```python
class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        left = 0
        right = len(nums)
        while left<right:
            mid = (left+right)//2
            if nums[mid]>=target:
                right = mid
            else:
                left = mid + 1
        return left 
```

本文链接：[https://www.jianshu.com/p/46b8d8a55888](https://www.jianshu.com/p/46b8d8a55888)
