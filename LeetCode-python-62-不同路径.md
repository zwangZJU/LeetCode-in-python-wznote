 [题目链接](https://leetcode-cn.com/problems/unique-paths/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
  一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。

问总共有多少条不同的路径？

 ![](https://upload-images.jianshu.io/upload_images/15048949-4b0912799cfb7edc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

**示例1**
> 输入: m = 3, n = 2
输出: 3
解释:
从左上角开始，总共有 3 条路径可以到达右下角。
1. 向右 -> 向右 -> 向下
2. 向右 -> 向下 -> 向右
3. 向下 -> 向右 -> 向右

**示例2**
> 输入: m = 7, n = 3
输出: 28

#### 解题思路
***
dp[i][j]表示走到第i行j列的不同路径数
走到matrix[i][j]只有两种途径，经过matrix[i-1][j]或matrix[i][j-1]
故得状态转移矩阵：
dp[i][j] = dp[i-1][j]+dp[i][j-1]


#### 代码实现
```
class Solution(object):
    def uniquePaths(self, m, n):
        """
        :type m: int
        :type n: int
        :rtype: int
        """
        dp = [[0]*m for _ in range(n)]
        for i in range(n):
            for j in range(m):
                if i==0 or j==0:
                    dp[i][j] = 1
                else:
                    dp[i][j] = dp[i-1][j]+dp[i][j-1]
                     
        return dp[n-1][m-1]
```

本文链接：[https://www.jianshu.com/p/5d3a08e5eb91](https://www.jianshu.com/p/5d3a08e5eb91)
