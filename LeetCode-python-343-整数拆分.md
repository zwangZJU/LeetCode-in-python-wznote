 [题目链接](https://leetcode-cn.com/problems/integer-break/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学、动态规划
***
 给定一个正整数 n，将其拆分为至少两个正整数的和，并使这些整数的乘积最大化。 返回你可以获得的最大乘积。

 
**示例1**
> 输入: 2
输出: 1
解释: 2 = 1 + 1, 1 × 1 = 1。

**示例2**
>输入: 10
输出: 36
解释: 10 = 3 + 3 + 4, 3 × 3 × 4 = 36。

#### 解题思路
***
 n<=3时，返回n-1
当n>=4时，最大乘积一定是由k个2和m个3组成的
dp[i]表示i拆分后的最大乘积，其中i>=4， 为了dp[4],dp[5],dp[6]能正常计算，需要初始化dp[0]=dp[1]=0,dp[2]=2,dp[3]=3
状态转移矩阵为dp[i] = max(dp[i-2]*2 , dp[i-3]*3)


#### 代码实现
```python
class Solution:
    def integerBreak(self, n: int) -> int:        
        if n<=3:
            return n-1
        dp = [0] * (n+1)
        dp[1:4] = [1, 2, 3]
        for i in range(4, n+1):            
            dp[i] = max(2*dp[i-2], 3*dp[i-3])         
        return dp[n]
```

本文链接：[https://www.jianshu.com/p/199a3c4f3f59](https://www.jianshu.com/p/199a3c4f3f59)
