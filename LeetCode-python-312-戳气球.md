[题目链接](https://leetcode-cn.com/problems/burst-balloons/description/)
难度： 困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：分治
***
有 n 个气球，编号为0 到 n-1，每个气球上都标有一个数字，这些数字存在数组 nums 中。

现在要求你戳破所有的气球。每当你戳破一个气球 i 时，你可以获得 nums[left] * nums[i] * nums[right] 个硬币。 这里的 left 和 right 代表和 i 相邻的两个气球的序号。注意当你戳破了气球 i 后，气球 left 和气球 right 就变成了相邻的气球。

求所能获得硬币的最大数量

**示例**
>输入: [3,1,5,8]
输出: 167 
解释: 
nums = [3,1,5,8] --> [3,5,8] --> [3,8] --> [8] --> [ ]
coins =  3\*1\*5      +  3\*5\*8    +  1\*3\*8      + 1\*8\*1   = 167
     
#### 解题思路
***
- 设dp[i][j]表示错破i到j之间的气球能得到的最大硬币数量。
- 假设k是最后一个被戳破的气球，i<k<j ,于是乎，如果我们从k处把序列断开为(i,k)和(k,j) 
- 那么 dp[i][j] = max(dp[i][k]+dp[k][j] + nums[i]\*nums[k]\*nums[j])

#### 代码实现
```
def maxCoins(iNums):
    nums = [1] + [i for i in iNums if i > 0] + [1]
    n = len(nums)
    dp = [[0]*n for _ in range(n)]

    for k in range(2, n):
        for left in range(0, n - k):
            right = left + k
            for i in range(left + 1,right):
                dp[left][right] = max(dp[left][right], nums[left] * nums[i] * nums[right] + dp[left][i] + dp[i][right])
    return dp[0][n - 1]
```

本文链接：[https://www.jianshu.com/p/ba0d6e431baa](https://www.jianshu.com/p/ba0d6e431baa)
