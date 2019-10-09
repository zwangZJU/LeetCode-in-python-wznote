 [题目链接](https://leetcode-cn.com/problems/all-paths-from-source-to-target/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组  、图
***
 给一个有 n 个结点的有向无环图，找到所有从 0 到 n-1 的路径并输出（不要求按顺序）

二维数组的第 i 个数组中的单元都表示有向图中 i 号结点所能到达的下一些结点（译者注：有向图是有方向的，即规定了a→b你就不能从b→a）空就是没有下一个结点了。



 
**示例**
> 输入: [[1,2], [3], [3], []] 
输出: [[0,1,3],[0,2,3]] 
解释: 图是这样的:
0--->1
|    |
v    v
2--->3
这有两条路: 0 -> 1 -> 3 和 0 -> 2 -> 3.


#### 解题思路
***
 target是len(graph)-1
source是0

graph[i]中的元素是i能到达的所有节点

从graph[0]开始，记录不断延申的路劲，直到路劲的最后一个值等于target为止



#### 代码实现
```
class Solution(object):
    def allPathsSourceTarget(self, graph):
        """
        :type graph: List[List[int]]
        :rtype: List[List[int]]
        """
        target = len(graph)-1
        res = []
        def find(nodes, path):
            if path[-1] == target:               
                    res.append(path)
            for i, node in enumerate(nodes):                            
                find(graph[node], path+[node])
        find(graph[0], [0])
        return res
```

本文链接：[https://www.jianshu.com/p/15fd4fd1af9c](https://www.jianshu.com/p/15fd4fd1af9c)
