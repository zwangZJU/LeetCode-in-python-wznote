 [题目链接](https://leetcode-cn.com/problems/01-matrix/）
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、广度优先搜索
***
 给定一个由 0 和 1 组成的矩阵，找出每个元素到最近的 0 的距离。

两个相邻元素间的距离为 1 。

 
**示例1**
> 输入:
0 0 0
0 1 0
0 0 0
输出:
0 0 0
0 1 0
0 0 0

**示例2**
> 输入:
0 0 0
0 1 0
1 1 1
输出:
0 0 0
0 1 0
1 2 1

#### 解题思路
***
 1. 先找出matrix中所有0的坐标,记录在队列q中，并将值为1的地方赋为n+m，应为最远的距离也不会超过n+m
2.遍历q中元素q[i]，跟新q[i]周围四个点的距离，更新了距离的点的坐标入队，直到遍历到q的最后一个元素为止



#### 代码实现
```
class Solution(object):
    def updateMatrix(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[List[int]]
        """
        
        n, m = len(matrix), len(matrix[0])
        max_val = n+m
        pos = []
        for i in range(n):
            for j in range(m):
                if matrix[i][j] == 0:
                    pos.append((i,j))
                else:
                    matrix[i][j] = max_val
        for i,j in pos:
            for r, c in [(i+1, j), (i-1,j), (i, j+1), (i, j-1)]:
                if 0<=r<n and 0<=c<m and matrix[i][j]+1<matrix[r][c]:
                    matrix[r][c] = matrix[i][j] + 1
                    pos.append((r, c))
        return matrix
```

本文链接：[https://www.jianshu.com/p/ccecb8547cc4](https://www.jianshu.com/p/ccecb8547cc4)
