 [题目链接](https://leetcode-cn.com/problems/find-the-duplicate-number/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组
***
给定一个包含 n + 1 个整数的数组 nums，其数字都在 1 到 n 之间（包括 1 和 n），可知至少存在一个重复的整数。假设只有一个重复的整数，找出这个重复的数。
**示例1**
>输入: [1,3,4,2,2]
输出: 2

**示例2**
>输入: [3,1,3,4,2]
输出: 3

#### 解题思路
***
将每一个数字k都放在数组的第k-1位上（如数字1放在第0位，数字3放在第2位），若该位上已有正确的数字，则该数位重复数

#### 代码实现
```
class Solution(object):
    def findDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        # write code here
        n = len(nums)
        i = 0
        while i<n:
            if nums[i] != i+1:
                if nums[nums[i]-1] == nums[i]:                  
                    return nums[i]
                else:          
                    nums[nums[i]-1], nums[i] =  nums[i], nums[nums[i]-1]
            else:
                i += 1
```

本文链接：[https://www.jianshu.com/p/a289b733e174](https://www.jianshu.com/p/a289b733e174)
