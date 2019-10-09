 [题目链接](https://leetcode-cn.com/problems/shortest-bridge/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  深度优先搜索、广度优先搜索
***
在给定的二维二进制数组 A 中，存在两座岛。（岛是由四面相连的 1 形成的一个最大组。）

现在，我们可以将 0 变为 1，以使两座岛连接起来，变成一座岛。

返回必须翻转的 0 的最小数目。（可以保证答案至少是 1。）
 
**示例1**
> 输入：[[0,1],[1,0]]
输出：1

**示例2**
>输入：[[0,1,0],[0,0,0],[0,0,1]]
输出：2

**示例3**
>输入：[[1,1,1,1,1],[1,0,0,0,1],[1,0,1,0,1],[1,0,0,0,1],[1,1,1,1,1]]
输出：1

#### 解题思路
***
 1. 遍历数组找到第一个为1的数
2. 以当前为1的坐标为起点进行深度优先搜索，找到第一个岛屿的全部范围，注意，每找到一个点要标记一下，以免重复寻找
3. 以第一个岛屿的所有坐标为起点，进行广度优先搜索，找到不属于该岛的第一个1，返回到达该点所搜索的次数，就为最短的桥，注意，找过的点也要标记一下，以免重复寻找

为了不重复需搜索，可以将搜索过的点的值改为-1



#### 代码实现
```python
class Solution(object):
    def shortestBridge(self, A):
        """
        :type A: List[List[int]]
        :rtype: int
        """    
        n, queue = len(A), []
        def dfs(x,y):   
            A[x][y] = -1
            queue.append((x,y))
            for i, j in [(x+1, y), (x-1, y), (x, y+1), (x, y-1)]:
                if 0<=i<n and 0<=j<n and A[i][j] == 1:
                    dfs(i, j)               
        def find_first_island():
            for i in range(n):
                for j in range(n):
                    if A[i][j] == 1:
                        dfs(i,j)
                        return
        find_first_island()
        count = 0
        while queue:
            t = []
            for x, y in queue:     
                for i, j in [(x+1, y), (x-1, y), (x, y+1), (x, y-1)]:
                    if 0<=i<n and 0<=j<n:
                        if  A[i][j]==1:
                            return count
                        elif A[i][j]==0:   
                            A[i][j] = -1
                            t.append((i, j))                           
            count += 1
            queue = t
```

本文链接：[https://www.jianshu.com/p/dc6780705433](https://www.jianshu.com/p/dc6780705433)
