 [题目链接](https://leetcode-cn.com/problems/longest-increasing-subsequence/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组，动态规划
***
给定一个无序的整数数组，找到其中最长上升子序列的长度

**示例**
>输入: [10,9,2,5,3,7,101,18]
输出: 4 
解释: 最长的上升子序列是 [2,3,7,101]，它的长度是 4

#### 解题思路
***
dp[i]表示到第i位时最长上升子序列的长度
为了更新dp[i]，需要找到以num[i]为最后一个元素的所有上升子序列，求出最长的长度
状态转移方程为：dp[i] = max(dp[j])+1,其中 0<j<i, 且nums[i]>nums[j]
若不存在nums[i]>nums[j],其中0<j<i, 则dp[i] =1

#### 代码实现
```
class Solution(object):
    def lengthOfLIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0    
        n = len(nums)
        dp = [1]*n
        for i in range(1,n):
            cur_max = 0
            for j in range(i):
                if nums[i]>nums[j]:
                    cur_max = max(cur_max, dp[j])   
            if cur_max:
                dp[i] = cur_max + 1         
        return max(dp)
```

本文链接：[https://www.jianshu.com/p/ab33e7a43fa5](https://www.jianshu.com/p/ab33e7a43fa5)
