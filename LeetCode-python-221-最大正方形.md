 [题目链接](https://leetcode-cn.com/problems/maximal-square/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 动态规划 
***
 在一个由 0 和 1 组成的二维矩阵内，找到只包含 1 的最大正方形，并返回其面积。

 
**示例**
>输入: 
1 0 1 0 0
1 0 1 1 1
1 1 1 1 1
1 0 0 1 0
输出: 4

#### 解题思路
***
按照逐行从左到右遍历matrix，
对于第k行的dp[i]，表示以matrix[k][i]做正方形的坐下定点是的最大面积。
pre为第k-1行的dp[i]
状态转移方程：
dp[i] = min(pre[i-1], pre[i], dp[i-1]) + 1

dp 和 pre初始化的时候都是m+1维全零向量，m=len(matrix[0])
从下标1开始赋值，这样可以保证pre[i-1]和dp[i-1]始终有值，并且pre[0]和dp[0]始终为0



#### 代码实现
```
class Solution:
    def maximalSquare(self, matrix: List[List[str]]) -> int:
        if not matrix:
            return 0
        n， m= len(matrix), len(matrix[0])
        dp = [0] * (m+1)
        pre = [0] * (m+1)
        max_val = 0
        for i in range(n):
            for j in range(m):
                if matrix[i][j] == '1':
                    dp[j+1] = min(min(pre[j], pre[j+1]), dp[j]) + 1
                    max_val = max(max_val, dp[j+1])
                else:
                    dp[j+1] = 0
            pre = dp[:]
        return max_val ** 2
```

本文链接：[https://www.jianshu.com/p/8dcff6adcf96](https://www.jianshu.com/p/8dcff6adcf96)
