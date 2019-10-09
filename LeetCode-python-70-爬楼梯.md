[题目链接](https://leetcode-cn.com/problems/climbing-stairs/description/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划
***
假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

**示例**
>输入： 3
输出： 3
解释：有三种方法可以爬到楼顶。
    1.  1 阶 + 1 阶 + 1 阶
    2.  1 阶 + 2 阶
    3.  2 阶 + 1 阶

#### 解题思路
***
- dp[i]表示爬到第i阶可以用得方法
- 跳上第i级台阶只有两种可能，一是从i-1级爬了一个台阶，二是从i-2级爬了2个台阶
- 可以得到状态转移方程：dp[i] = dp[i-1] + dp[i-2]
#### 代码实现
```
class Solution:
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        if n <=2:
            return n
        dp = [0]*n
        dp[0] = 1
        dp[1] = 2
        for i in range(2,n):
            dp[i] = dp[i-1] + dp[i-2]
        return dp[n-1]
```

本文链接：[https://www.jianshu.com/p/7987c2d62462](https://www.jianshu.com/p/7987c2d62462)
