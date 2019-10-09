 [题目链接](https://leetcode-cn.com/problems/coloring-a-border/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、深度优先搜索
***
 给出一个二维整数网格 grid，网格中的每个值表示该位置处的网格块的颜色。

只有当两个网格块的颜色相同，而且在四个方向中任意一个方向上相邻时，它们属于同一连通分量。

连通分量的边界是指连通分量中的所有与不在分量中的正方形相邻（四个方向上）的所有正方形，或者在网格的边界上（第一行/列或最后一行/列）的所有正方形。

给出位于 (r0, c0) 的网格块和颜色 color，使用指定颜色 color 为所给网格块的连通分量的边界进行着色，并返回最终的网格 grid 。
 
 
**示例1**
> 输入：grid = [[1,1],[1,2]], r0 = 0, c0 = 0, color = 3
输出：[[3, 3], [3, 2]]

**示例2**
>输入：grid = [[1,2,2],[2,3,2]], r0 = 0, c0 = 1, color = 3
输出：[[1, 3, 3], [2, 3, 3]]

**示例3**
>输入：grid = [[1,1,1],[1,1,1],[1,1,1]], r0 = 1, c0 = 1, color = 2
输出：[[2, 2, 2], [2, 1, 2], [2, 2, 2]]

 
#### 解题思路
***
 只要四个边不全，就上色



#### 代码实现
```python
class Solution(object):
    def colorBorder(self, grid, r0, c0, color):
        """
        :type grid: List[List[int]]
        :type r0: int
        :type c0: int
        :type color: int
        :rtype: List[List[int]]
        """
        old_color = grid[r0][c0]
        new_color = color
        n, m = len(grid), len(grid[0])
        seen = set()
        def dfs(i,j):
            if (i,j) in seen: return True
            if not (0<=i<n and 0<=j<m and grid[i][j] == old_color):
                return False
            seen.add((i,j))
            if  dfs(i+1, j) + dfs(i-1, j) + dfs(i, j+1) + dfs(i, j-1)<4:
                    
                grid[i][j] = new_color
            return True
                
        dfs(r0, c0)
        return grid
```

本文链接：[https://www.jianshu.com/p/48a5e8c255ae](https://www.jianshu.com/p/48a5e8c255ae)
