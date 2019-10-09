 [题目链接](https://leetcode-cn.com/problems/minimum-path-sum/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
 给定一个包含非负整数的 m x n 网格，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小。

说明：每次只能向下或者向右移动一步。

 
**示例**
> 输入:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
输出: 7
解释: 因为路径 1→3→1→1→1 的总和最小。

#### 解题思路
***
到达每一个格子只有两种方法，左边向右走一步和上面向下走一步
dp[i][j]表示从（0，0）到达（i，j）的最小路径和
状态转移方程：
dp[i][j] = min(dp[i][j-1], dp[i-1][j]) + grid[i][j]

最后返回dp[-1][-1]即可 



#### 代码实现
```python
class Solution(object):
    def minPathSum(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        y = len(grid[0])
        x = len(grid)
        dp = [[0]*y for _ in range(x)]
        dp[0][0] = grid[0][0]
        for i in range(1,x):
            dp[i][0] = dp[i-1][0]+grid[i][0]
        for j in range(1,y):
            dp[0][j] = dp[0][j-1]+ grid[0][j]
            
        for i in range(1,len(grid)):
            for j in range(1,len(grid[0])):
                dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + grid[i][j]
        
        return dp[x-1][y-1]
```

本文链接：[https://www.jianshu.com/p/78a4a848e963](https://www.jianshu.com/p/78a4a848e963)
