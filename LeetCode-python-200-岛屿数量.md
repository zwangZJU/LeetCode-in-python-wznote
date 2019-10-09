 [题目链接](https://leetcode-cn.com/problems/number-of-islands/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  深度优先搜索
***
给定一个由 '1'（陆地）和 '0'（水）组成的的二维网格，计算岛屿的数量。一个岛被水包围，并且它是通过水平方向或垂直方向上相邻的陆地连接而成的。你可以假设网格的四个边均被水包围。

 
**示例1**
> 输入:
11110
11010
11000
00000
输出: 1

**示例2**
>输入:
11000
11000
00100
00011
输出: 3

#### 解题思路
***
1. 遍历这个网格，当有一格内是‘1’时，以此为起点，向四个方向进行深度优先搜索（广度优先搜索也行），找到所有能到达的‘1’，搜索过的地方用‘#’标记，以免重复搜索，无法及继续搜索时代表已经找到一个完整的岛屿。
2. 继续遍历网格，重复第1步，直到网格遍历完



#### 代码实现
```python
class Solution(object):
    def numIslands(self, grid):
        """
        :type grid: List[List[str]]
        :rtype: int
        """
        count = 0
        for i in range(len(grid)):
            for j in range(len(grid[0])):
                
                if grid[i][j] == '1':
                    self.dfs(grid, i,j)
                    count += 1
                    
        return count
    
    def dfs(self, grid, i, j):
        if i<0 or j<0 or i>=len(grid) or j>=len(grid[0]) or grid[i][j] != '1':
            return
        grid[i][j] = '#'
        self.dfs(grid, i+1, j)
        self.dfs(grid, i-1, j)
        self.dfs(grid, i, j+1)
        self.dfs(grid, i, j-1)
            
```
本文链接：[https://www.jianshu.com/p/248896a06498](https://www.jianshu.com/p/248896a06498)

 
