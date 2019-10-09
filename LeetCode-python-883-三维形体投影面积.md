 [题目链接](https://leetcode-cn.com/problems/projection-area-of-3d-shapes/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组、数学  
***
 在 N * N 的网格中，我们放置了一些与 x，y，z 三轴对齐的 1 * 1 * 1 立方体。

每个值 v = grid[i][j] 表示 v 个正方体叠放在单元格 (i, j) 上。

现在，我们查看这些立方体在 xy、yz 和 zx 平面上的投影。

投影就像影子，将三维形体映射到一个二维平面上。

在这里，从顶部、前面和侧面看立方体时，我们会看到“影子”。

返回所有三个投影的总面积。

 

 
**示例1**
> 输入：[[2]]
输出：5 

**示例2**
> 输入：[[1,2],[3,4]]
输出：17
解释：
这里有该形体在三个轴对齐平面上的三个投影(“阴影部分”)。

**示例3**
>输入：[[1,0],[0,2]]
输出：8

**示例4**
>输入：[[1,1,1],[1,0,1],[1,1,1]]
输出：14

**示例5**
>输入：[[2,2,2],[2,1,2],[2,2,2]]
输出：21

#### 解题思路
***
 从顶部看，由该形状生成的阴影将是网格中非零值的数目。

从侧面看，由该形状生成的阴影将是网格中每一行的最大值。

从前面看，由该形状生成的阴影将是网格中每一列的最大值。

 


#### 代码实现
```python
class Solution(object):
    def projectionArea(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        res = top = 0
        n = len(grid)
         
        for i in range(n):
            side, front = max(grid[i]), 0
            for j in range(n):
                if grid[j][i]:
                    top += 1                
                    front = max(front, grid[j][i])
            res += side + front
        return res + top
            
```

本文链接：[https://www.jianshu.com/p/98de5eab6fcd](https://www.jianshu.com/p/98de5eab6fcd)
