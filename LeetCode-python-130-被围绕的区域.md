[题目链接](https://leetcode-cn.com/problems/surrounded-regions/)

难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个二维的矩阵，包含 'X' 和 'O'（字母 O）。

找到所有被 'X' 围绕的区域，并将这些区域里所有的 'O' 用 'X' 填充。

 
**示例**
> 输入
X X X X
X O O X
X X O X
X O X X
输出
X X X X
X X X X
X X X X
X O X X
解释:
被围绕的区间不会存在于边界上，换句话说，任何边界上的 'O' 都不会被填充为 'X'。 任何不在边界上，或不与边界上的 'O' 相连的 'O' 最终都会被填充为 'X'。如果两个元素在水平或垂直方向相邻，则称它们是“相连”的。

#### 解题思路
***
 BFS:
搜索二维矩阵边界上的‘O'，再以此’O'为起点广度优先搜索，所到之处全部标记为‘T'
如示例中的输入就变为：
X X X X                   
X O O X
X X O X       
X T X X
遍历数组，将'O'替换为’X','T‘替换为’X',即可


#### 代码实现
```
class Solution:
    def solve(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        
        r = len(board)
        if not r:
            return 
        c = len(board[0])
        
        def bfs(board, i, j):
            if 0<=i<r and 0<=j<c and board[i][j] == 'O':
                board[i][j] = 'T'
                bfs(board, i, j+1)
                bfs(board, i, j-1)
                bfs(board, i+1, j)
                bfs(board, i-1, j)
        
       
        for i in range(r):
            for j in range(c):
                if (i==0 or i==r-1 or j==0 or j==c-1)  and board[i][j]=='O':
                    bfs(board, i, j)
        
        for i in range(r):
            for j in range(c):
                board[i][j] = 'O' if board[i][j]=='T' else 'X'
```

本文链接：[https://www.jianshu.com/p/57fe538a210f](https://www.jianshu.com/p/57fe538a210f)
