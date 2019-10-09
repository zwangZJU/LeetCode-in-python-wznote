 [题目链接](https://leetcode-cn.com/problems/minimum-falling-path-sum/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
 给定一个方形整数数组 A，我们想要得到通过 A 的下降路径的最小和。

下降路径可以从第一行中的任何元素开始，并从每一行中选择一个元素。在下一行选择的元素和当前行所选元素最多相隔一列。

 
**示例**
> 输入：[[1,2,3],[4,5,6],[7,8,9]]
输出：12
解释：
可能的下降路径有：
[1,4,7], [1,4,8], [1,5,7], [1,5,8], [1,5,9]
[2,4,7], [2,4,8], [2,5,7], [2,5,8], [2,5,9], [2,6,8], [2,6,9]
[3,5,7], [3,5,8], [3,5,9], [3,6,8], [3,6,9]

 
#### 解题思路
***
 dp[i][j] 表示走到A的第i行j列时的最小和
状态转移方程：
dp[i][j] = A[i][j] + min(dp[i-1][j-1], dp[i-1][j], dp[i-1][j+1])



#### 代码实现
```python
class Solution(object):
    def minFallingPathSum(self, A):
        """
        :type A: List[List[int]]
        :rtype: int
        """
        n, m = len(A), len(A[0])
        dp = [[0]*m for _ in range(n)]
        dp[0] = A[0]
        for i in range(1, n):
            for j in range(m):
                dp[i][j] = A[i][j] + min(dp[i-1][max(j-1,0)], dp[i-1][j], dp[i-1][min(j+1, m-1)])         
        return min(dp[-1])
```

本文链接：[https://www.jianshu.com/p/3eb3f63f7136](https://www.jianshu.com/p/3eb3f63f7136)
