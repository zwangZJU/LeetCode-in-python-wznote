 [题目链接](https://leetcode-cn.com/problems/rotting-oranges/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、广度优先搜索
***
 在给定的网格中，每个单元格可以有以下三个值之一：

值 0 代表空单元格；
值 1 代表新鲜橘子；
值 2 代表腐烂的橘子。
每分钟，任何与腐烂的橘子（在 4 个正方向上）相邻的新鲜橘子都会腐烂。

返回直到单元格中没有新鲜橘子为止所必须经过的最小分钟数。如果不可能，返回 -1。

 
**示例1**
> 输入：[[2,1,1],[1,1,0],[0,1,1]]
输出：4

**示例2**
>输入：[[2,1,1],[0,1,1],[1,0,1]]
输出：-1
解释：左下角的橘子（第 2 行， 第 0 列）永远不会腐烂，因为腐烂只会发生在 4 个正向上。

**示例2**
>输入：[[0,2]]
输出：0
解释：因为 0 分钟时已经没有新鲜橘子了，所以答案就是 0 。

#### 解题思路
***
 遍历数组，记录初始的所有腐烂橘子的位置

遍历这些位置，将周围腐烂，并记录被腐烂的位置，再遍历这些位置，重复操作，直到没有新的被腐烂的橘子出现



#### 代码实现
```python
class Solution(object):
    def orangesRotting(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
         
        n, m = len(grid), len(grid[0])
        d = [[0,1], [0,-1], [1,0],[-1,0]]
        rots = []
        for i in range(n):
            for j in range(m):
                if grid[i][j] == 2:
                    rots.append([i,j])
        res = 0
        
        while rots:
            t = []
            for _, (x, y) in enumerate(rots):
                for _, (dx, dy) in enumerate(d):
                    i, j = x+dx, y+dy
                    if 0<=i<n and 0<=j<m and grid[i][j] == 1:
                     
                        grid[i][j] = 2
                        t.append([i,j])
            
            rots = t
          
            res += 1
       
        if any(1 in row for row in grid):
            return -1
        return max(0,res-1)
```

本文链接：[https://www.jianshu.com/p/17be517354a6](https://www.jianshu.com/p/17be517354a6)
