[题目链接](https://leetcode-cn.com/problems/house-robber/description/)
难度： 简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划
***
你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。

给定一个代表每个房屋存放金额的非负整数数组，计算你在不触动警报装置的情况下，能够偷窃到的最高金额。

**示例**
>输入: [2,7,9,3,1]
输出: 12
解释: 偷窃 1 号房屋 (金额 = 2), 偷窃 3 号房屋 (金额 = 9)，接着偷窃 5 号房屋 (金额 = 1)。
     偷窃到的最高金额 = 2 + 9 + 1 = 12 。
     
#### 解题思路
***
- dp[i]的含义为到第i家店小偷能偷到的最高金额
- 到第i家店时有两种可能性，一是偷，二是不偷，为了不会报警，偷时必须保证i-1家店没被偷，该情况偷得得金额为dp[i-2]+nums[i]，若不偷，此时得金额等于dp[i-1]
- 得到状态转移方程： dp[i] = max(dp[i-2]+nums[i], dp[i-1])
#### 代码实现
```
class Solution:
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        elif len(nums)<=2:
            return max(nums)
        dp = [0 for _ in range(len(nums))]
        dp[0] = nums[0]
        dp[1] = max(nums[:2])
        for i in range(2, len(nums)):
            dp[i] = max(dp[i-2]+nums[i],dp[i-1])     
        return dp[i]
```

本文链接：[https://www.jianshu.com/p/308ae8b9ab6b](https://www.jianshu.com/p/308ae8b9ab6b)
