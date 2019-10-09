 [题目链接](https://leetcode-cn.com/problems/previous-permutation-with-one-swap/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  Dijkstra
***
有 n 个城市通过 m 个航班连接。每个航班都从城市 u 开始，以价格 w 抵达 v。

现在给定所有的城市和航班，以及出发城市 src 和目的地 dst，你的任务是找到从 src 到 dst 最多经过 k 站中转的最便宜的价格。 如果没有这样的路线，则输出 -1。
 
**示例1**
> 输入: 
n = 3, edges = [[0,1,100],[1,2,100],[0,2,500]]
src = 0, dst = 2, k = 1
输出: 200
解释: 
从城市 0 到城市 2 在 1 站中转以内的最便宜价格是 200

**示例2**
> 输入: 
n = 3, edges = [[0,1,100],[1,2,100],[0,2,500]]
src = 0, dst = 2, k = 0
输出: 500

 
#### 解题思路
***
 最短路径，标准的Dijkstra算法
graph用于存储src, dst, cost，结构为{s:{d1:cost1, d2:cost2}}
heap用于存储当前能到达的城市d的相关信息，结构为(cost, d, k)，cost为到达d的花费，k为还能中转的次数

1. 先建立有向图，存储在字典里
2. 从起始点开始，找到所有起点城市s能飞到的城市d，若还有中转的次数（k>0），更新从起点到达这些城市的价格，根据价格建立最小堆。如果d中包含目的地，直接返回到达目的地的cost
3. 取出当前花费最小的能到达的城市作为新起点s，进行第2步，进行该步直到所有节点遍历完毕



#### 代码实现
```python
import collections
import heapq
class Solution(object):
    def findCheapestPrice(self, n, flights, src, dst, K):
        """
        :type n: int
        :type flights: List[List[int]]
        :type src: int
        :type dst: int
        :type K: int
        :rtype: int
        """
        graph = collections.defaultdict(dict)
        heap = [(0, src, K+1)]
        for s,d,c in flights:
            graph[s][d] = c
        while heap:
            cost, s, k = heapq.heappop(heap)
            if s == dst: return cost
            if k > 0: 
                for d in graph[s]:
                    heapq.heappush(heap, (cost+graph[s][d], d, k-1))
        return -1
```

本文链接：[https://www.jianshu.com/p/664206735378](https://www.jianshu.com/p/664206735378)
