 [题目链接](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二分搜索
***
 假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

搜索一个给定的目标值，如果数组中存在这个目标值，则返回它的索引，否则返回 -1 。

你可以假设数组中不存在重复的元素。

你的算法时间复杂度必须是 O(log n) 级别。
 
**示例1**
> 输入: nums = [4,5,6,7,0,1,2], target = 0
输出: 4

**示例2**
>输入: nums = [4,5,6,7,0,1,2], target = 3
输出: -1

#### 解题思路
***
 看到这种有序的数组就会想到二分搜索
主要分两种情况：
1. 若nums[left]<=nums[mid]，这说明前半部分是排序的
若nums[left]<=target<=nums[mid]，在前半部分搜索，反之在后半部分搜索
2. 若nums[left]>nums[mid]，这说明后半部分是排序的
若nums[mid]<=target<=nums[right]，在后半部分搜索，反之在前半部分搜索
一直搜索，直到left>=right

#### 代码实现
```python
class Solution(object):
    def search(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        n = len(nums)
        left, right = 0, n-1
        while left<right:
            mid = (left+right)//2
            if nums[mid] == target: 
                return mid
            if nums[left] <= nums[mid]:
                if nums[left] <= target <= nums[mid]:
                    right = mid
                else:
                    left = mid + 1
            else:
                if nums[mid] <= target <= nums[right]:
                    left = mid + 1
                else:
                    right = mid

        return left if nums and nums[left]==target else -1
```

本文链接：[https://www.jianshu.com/p/7295418b260f](https://www.jianshu.com/p/7295418b260f)
