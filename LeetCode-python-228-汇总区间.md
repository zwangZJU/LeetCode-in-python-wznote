 [题目链接](https://leetcode-cn.com/problems/summary-ranges/submissions/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组
***

**示例1**
>输入: [0,1,2,4,5,7]
输出: ["0->2","4->5","7"]
解释: 0,1,2 可组成一个连续的区间; 4,5 可组成一个连续的区间。

**示例2**
>输入: [0,2,3,4,6,8,9]
输出: ["0","2->4","6","8->9"]
解释: 2,3,4 可组成一个连续的区间; 8,9 可组成一个连续的区间。

#### 解题思路
***
双指针，记录每个区间的start和end
当nums[i]-nums[i-1]不等于1时，说明不连续，此时需要将上一个区间保存，并且更新start和end均为nums[i]
当nums[i]-nums[i-1]等于1时,说明连续，让end指向nums[i]

保存区间有两种情况，一种是start和end指向同一个数，此时保存start; 另一种是指向不同的数，此时保存start+'->'+end

数组遍历完后还需要保存最后一个区间

#### 代码实现
```
class Solution(object):
    def summaryRanges(self, nums):
        """
        :type nums: List[int]
        :rtype: List[str]
        """
        if not nums:
            return []
        n = len(nums)
        start = end = str(nums[0])
        res = []
        for i in range(1,n):
            if nums[i] - nums[i-1] == 1:
                end = str(nums[i])
            else:              
                if start == end:
                    res.append(start)
                else:
                    res.append(start+'->'+end)
                start = end = str(nums[i])           
        if start == end:
            res.append(start)
        else:
            res.append(start+'->'+end)
        return res
```

本文链接：[https://www.jianshu.com/p/3cf34c6691d5](https://www.jianshu.com/p/3cf34c6691d5)
