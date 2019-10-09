 [题目链接](https://leetcode-cn.com/problems/unique-paths-ii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。

现在考虑网格中有障碍物。那么从左上角到右下角将会有多少条不同的路径？

 ![](https://upload-images.jianshu.io/upload_images/15048949-4b0912799cfb7edc.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 
**示例**
> 输入:
[
  [0,0,0],
  [0,1,0],
  [0,0,0]
]
输出: 2
解释:
3x3 网格的正中间有一个障碍物。
从左上角到右下角一共有 2 条不同的路径：
1.向右 -> 向右 -> 向下 -> 向下
2.向下 -> 向下 -> 向右 -> 向右

 
#### 解题思路
***
 dp[i][j]表示走到第i行j列的不同路径数
走到matrix[i][j]只有两种途径，经过matrix[i-1][j]或matrix[i][j-1]
故得状态转移矩阵：
dp[i][j] = dp[i-1][j]+dp[i][j-1]

但是，遇到障碍物时，dp[i][j]=0


#### 代码实现
```python
class Solution(object):
    def uniquePathsWithObstacles(self, obstacleGrid):
        """
        :type obstacleGrid: List[List[int]]
        :rtype: int
        """
        row = len(obstacleGrid)
        col = len(obstacleGrid[0])
        dp = [[0]*col for _ in range(row)]
        if obstacleGrid[0][0] == 0:
            dp[0][0] = 1
           
        for i in range(row):
            for j in range(col):
                if obstacleGrid[i][j] == 1:
                    dp[i][j] = 0
                elif i==0 and j>0:
                    dp[i][j] = dp[i][j-1]
                elif j==0 and i>0:
                    dp[i][j] = dp[i-1][j]
                elif j==0 and i==0:
                    dp[i][j] = 1
                else:
                    dp[i][j] = dp[i-1][j] + dp[i][j-1]
                
        return dp[row-1][col-1] 
```

本文链接：[https://www.jianshu.com/p/4a78d8433630](https://www.jianshu.com/p/4a78d8433630)
