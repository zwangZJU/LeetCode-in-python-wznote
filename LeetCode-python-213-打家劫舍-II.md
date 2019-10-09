 [题目链接](https://leetcode-cn.com/problems/house-robber-ii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、动态规划
***
 你是一个专业的小偷，计划偷窃沿街的房屋，每间房内都藏有一定的现金。这个地方所有的房屋都围成一圈，这意味着第一个房屋和最后一个房屋是紧挨着的。同时，相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。

给定一个代表每个房屋存放金额的非负整数数组，计算你在不触动警报装置的情况下，能够偷窃到的最高金额。
 
 
**示例1**
> 输入: [2,3,2]
输出: 3
解释: 你不能先偷窃 1 号房屋（金额 = 2），然后偷窃 3 号房屋（金额 = 2）, 因为他们是相邻的。

**示例2**
> 输入: [1,2,3,1]
输出: 4
解释: 你可以先偷窃 1 号房屋（金额 = 1），然后偷窃 3 号房屋（金额 = 3）。
     偷窃到的最高金额 = 1 + 3 = 4 。

 
#### 解题思路
***
思路 同[198.打家劫舍](https://www.jianshu.com/p/308ae8b9ab6b)
关键在于选不选第一家
所以可以将原数组分成两种情况
1. 没有第一家
2. 没有最后一家
这样就可以按198题做了，最后求两种情况的最大值


#### 代码实现
```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        if not nums: return 0
        if len(nums)<=3: return max(nums)
        return max(self.get_max(nums[1:]), self.get_max(nums[:-1]))
        
    def get_max(self, nums):
        n = len(nums)
        dp = [0] * n
        dp[0] = nums[0]
        dp[1] = max(nums[:2])
        for i in range(2,n):
            dp[i] = max(dp[i-2]+nums[i], dp[i-1])       
        return dp[-1]
```

本文链接：[https://www.jianshu.com/p/e998e70a18d2](https://www.jianshu.com/p/e998e70a18d2)
