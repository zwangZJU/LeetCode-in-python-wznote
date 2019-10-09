 [题目链接](https://leetcode-cn.com/problems/maximum-subarray/)
难度：简单       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、动态规划
***
 
给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。
 
**示例**
> 输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。

#### 解题思路
***
 dp[i]表示到第i为时由第i个数为序列最后一个数时的最大和
若dp[i-1]>0,果断连起来
反之，以当前数位序列的第一个数

每一位时都记录到目前为止最大的子序列和



#### 代码实现
```
class Solution(object):
    def maxSubArray(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        max_val = nums[0]
        dp = [0] * len(nums)
        dp[0] = nums[0]
        for i in range(1, len(nums)):
            if dp[i-1]>0:
                dp[i] = dp[i-1]+nums[i]
            else:
                dp[i] = nums[i]
            max_val = max(max_val, dp[i])
        return max_val
```

本文链接：[https://www.jianshu.com/p/1e0b70c56548](https://www.jianshu.com/p/1e0b70c56548)
