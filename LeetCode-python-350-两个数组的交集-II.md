[题目链接](https://leetcode-cn.com/problems/intersection-of-two-arrays-ii/)

难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定两个数组，编写一个函数来计算它们的交集。

 
**示例1**
> 输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2,2]

**示例2**
> 输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出: [4,9]

#### 解题思路
***
 统计nums1中的数字及其个数
遍历nums2，当nums2[i]在nums1中，且个数大于0，添加到结果中
若不在或个数等于0，则不添加



#### 代码实现
```
import collections
class Solution:
    def intersect(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """
        nums1 = collections.Counter(nums1)
        res = []
        for num in nums2:
            if num in nums1 and nums1[num]>0:
                res.append(num)
                nums1[num] -= 1
        return res
```

本文链接：[https://www.jianshu.com/p/f20bc1331387](https://www.jianshu.com/p/f20bc1331387)
