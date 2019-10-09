 [题目链接](https://leetcode-cn.com/problems/as-far-from-land-as-possible/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  广度优先搜索
***
 你现在手里有一份大小为 N x N 的『地图』（网格） grid，上面的每个『区域』（单元格）都用 0 和 1 标记好了。其中 0 代表海洋，1 代表陆地，你知道距离陆地区域最远的海洋区域是是哪一个吗？请返回该海洋区域到离它最近的陆地区域的距离。

我们这里说的距离是『曼哈顿距离』（ Manhattan Distance）：(x0, y0) 和 (x1, y1) 这两个区域之间的距离是 |x0 - x1| + |y0 - y1| 。

如果我们的地图上只有陆地或者海洋，请返回 -1。
 
**示例1**
> 输入：[[1,0,1],[0,0,0],[1,0,1]]
输出：2
解释： 
海洋区域 (1, 1) 和所有陆地区域之间的距离都达到最大，最大距离为 2。

**示例2**
>输入：[[1,0,0],[0,0,0],[0,0,0]]
输出：4
解释： 
海洋区域 (2, 2) 和所有陆地区域之间的距离都达到最大，最大距离为 4。

#### 解题思路
***
1. 先找到grid中所有的1的位置，保存在queue中，若全是1或者没有1，返回-1
2. 从这些1所在的位置开始进行广度优先搜索，即搜索四个方向，如果搜索的位置上的值为0，保存这些坐标，作为下一次搜索的起点，并将这些位置的值设置为1，以免重复搜索。这样每扩散一层，计数器加1，直到没有可搜索的起点，返回计数器的值就为最远的距离


#### 代码实现
```python
class Solution(object):
     def maxDistance(self, grid):
        """
        :type grid: List[List[int]]
        :rtype: int
        """
        n = len(grid)
        queue = [(i,j) for i in range(n) for j in range(n) if grid[i][j] == 1]
        if len(queue) == n * n or not queue: return -1
        level = 0
        while queue:
            t = []
            for x,y in queue:
                for i,j in [(x+1,y), (x-1, y), (x, y+1), (x, y-1)]:
                    if 0 <= i < n and 0 <= j < n and grid[i][j] == 0:
                        t.append((i, j))
                        grid[i][j] = 1
            queue = t
            level += 1
        return level-1
```

本文链接：[https://www.jianshu.com/p/ea5c190f412f](https://www.jianshu.com/p/ea5c190f412f)
