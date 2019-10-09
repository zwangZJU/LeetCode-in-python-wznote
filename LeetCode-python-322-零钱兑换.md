 [题目链接](https://leetcode-cn.com/problems/coin-change/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划 
***
 给定不同面额的硬币 coins 和一个总金额 amount。编写一个函数来计算可以凑成总金额所需的最少的硬币个数。如果没有任何一种硬币组合能组成总金额，返回 -1。
 
**示例1**
> 输入: coins = [1, 2, 5], amount = 11
输出: 3 
解释: 11 = 5 + 5 + 1

**示例2**
>输入: coins = [2], amount = 3
输出: -1

#### 解题思路
***
 dp[i]表示凑成总金额i需要的最少硬币个数

如例1中coins=[1,2,5]，dp[1],dp[2]和dp[5]都等于1，因为用相应金额的一枚硬币就能组成i。

对于其他的i,例如i = 11, dp[11] = min(dp[11-1], dp[11-2], dp[11-5])+1

dp[i]只有这两种更新方式 ，有可能amount无法用coins里的硬币构成，那么，初始化每个dp[i]的时候都为amount,若dp[amount]=amount,返回-1



#### 代码实现
```python
class Solution(object):
    def coinChange(self, coins, amount):
        """
        :type coins: List[int]
        :type amount: int
        :rtype: int
        """
        dp = [0]*(amount+1)
        coins.sort()
        for i in range(1,amount+1):
            if i in coins:
                dp[i] = 1
                continue
            min_val = amount
            for coin in coins:
                if i>=coin:
                    min_val = min(min_val, dp[i-coin])
                else:
                    break
            
            dp[i] = min_val+1 
        
        return dp[amount] if dp[amount]<=amount else -1
```

本文链接：[https://www.jianshu.com/p/9a06b438f341](https://www.jianshu.com/p/9a06b438f341)
