[题目链接](https://leetcode-cn.com/problems/intersection-of-two-arrays/)

难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定两个数组，编写一个函数来计算它们的交集。

 
**示例1**
>输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2] 

**示例2**
>输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出: [9,4]

#### 解题思路
***
 两个数组分别求集合
让小集合为nums1,大集合为nums2
遍历nums1,查看其中的元素是否在nums2中，若在则记录下来



#### 代码实现
```
class Solution:
    def intersection(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        nums1 = set(nums1)
        nums2 = set(nums2)
        if len(nums1)<len(nums2):
            nums1, nums2 = nums2, nums1
        return [x for x in nums1 if x in nums2]
```

本文链接：[https://www.jianshu.com/p/2edeaa136eaa](https://www.jianshu.com/p/2edeaa136eaa)
