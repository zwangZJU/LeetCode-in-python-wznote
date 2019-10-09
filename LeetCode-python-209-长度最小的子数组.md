[题目链接](https://leetcode-cn.com/problems/minimum-size-subarray-sum/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组
***
给定一个含有 n 个正整数的数组和一个正整数 s ，找出该数组中满足其和 ≥ s 的长度最小的连续子数组。如果不存在符合条件的连续子数组，返回 0。

**示例**
>输入: s = 7, nums = [2,3,1,2,4,3]
输出: 2
解释: 子数组 [4,3] 是该条件下的长度最小的连续子数组。

#### 解题思路
***
初始化，最小长度为min_val = n，当前总和cur_sum=0，
双指针，计算start到end之间的和:
若cur_sum $< $ s，end + 1
若cur_sum $\geq $ s，将end-start+1与min_val中更小的值赋给min_val
    将 cur_sum-nums[start]且start+1，直到cur_sum<s

#### 代码实现
```
class Solution(object):
    def minSubArrayLen(self, s, nums):
        """
        :type s: int
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        start = 0
        min_len = n+1
        cur_sum = 0
        for i in range(n):
            cur_sum += nums[i]
            while cur_sum >= s:
                min_len = min(min_len, i-start+1)
                cur_sum -= nums[start]
                start += 1
        return min_len if min_len<=n else 0
```

本文链接：[https://www.jianshu.com/p/24eb3a8df50b](https://www.jianshu.com/p/24eb3a8df50b)
