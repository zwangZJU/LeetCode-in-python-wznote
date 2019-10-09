 [题目链接](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、二分搜索
***
 假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

请找出其中最小的元素。

你可以假设数组中不存在重复元素。
 
 
**示例1**
> 输入: [3,4,5,1,2]
输出: 1

**示例2**
> 输入: [4,5,6,7,0,1,2]
输出: 0

#### 解题思路
***
 二分搜索：
移动右指针到mid的条件：
nums[mid]<nums[left]或者nums[mid]<nums[right]
不符合上述条件时移动左指针到mid+1



#### 代码实现
```
class Solution(object):
    def findMin(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        left, right = 0, len(nums)-1
        while left<right:
            mid = left + (right-left)//2
            if nums[mid]<nums[left] or nums[mid]<nums[right]:
                right = mid
            else:
                left = mid+1
        return nums[left]
```

本文链接：[https://www.jianshu.com/p/78990deaec15](https://www.jianshu.com/p/78990deaec15)
