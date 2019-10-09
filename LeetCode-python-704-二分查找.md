 [题目链接](https://leetcode-cn.com/problems/binary-search/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、二分查找
***
 给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target  ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。

 
**示例1**
> 输入: nums = [-1,0,3,5,9,12], target = 9
输出: 4
解释: 9 出现在 nums 中并且下标为 4

**示例2**
> 输入: nums = [-1,0,3,5,9,12], target = 2
输出: -1
解释: 2 不存在 nums 中因此返回 -1


#### 代码实现
```
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        left, right = 0, len(nums)-1
        while left<right:
            mid = left+(right-left)//2
            if nums[mid] == target:
                return mid
            if nums[mid]>target:
                right = mid - 1 
            else:
                left = mid + 1
        return left if nums[left]==target else -1
```

本文链接：[https://www.jianshu.com/p/af8db4b6ad47](https://www.jianshu.com/p/af8db4b6ad47)
