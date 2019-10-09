 [题目链接](https://leetcode-cn.com/problems/bus-routes/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  广度优先搜索
***
 我们有一系列公交路线。每一条路线 routes[i] 上都有一辆公交车在上面循环行驶。例如，有一条路线 routes[0] = [1, 5, 7]，表示第一辆 (下标为0) 公交车会一直按照 1->5->7->1->5->7->1->... 的车站路线行驶。

假设我们从 S 车站开始（初始时不在公交车上），要去往 T 站。 期间仅可乘坐公交车，求出最少乘坐的公交车数量。返回 -1 表示不可能到达终点车站。
 
**示例**
> 输入: 
routes = [[1, 2, 7], [3, 6, 7]]
S = 1
T = 6
输出: 2
解释: 
最优策略是先乘坐第一辆公交车到达车站 7, 然后换乘第二辆公交车到车站 6。
 
#### 解题思路
***
1. 用字典保存在每一站能上的车号，如{站：[车1， 车2]}
2.  用队列保存换乘第n次时能到达的所有站，再以这些站为起点，选择能坐且没做过的车，将这些车能到达的站加入队列
- 直到有一个能到达的站为T，返回换乘的次数n+1
- 直到无车可坐却还没到达，返回-1

为了不重复搜索，用set保存坐过的车，坐过就不再坐了



#### 代码实现
```python
class Solution(object):
    def numBusesToDestination(self, routes, S, T):
        """
        :type routes: List[List[int]]
        :type S: int
        :type T: int
        :rtype: int
        """
        if S==T:
            return 0
        stop_board = {}
        for bus, stations in enumerate(routes):
            for station in stations:
                if station not in stop_board:
                    stop_board[station] = [bus]
                else:
                    stop_board[station].append(bus)
        
        queue = [S]
        visited = set()
        res = 0
        while queue:
            t = []
            res += 1
            for station in queue:
                for bus in stop_board[station]:
                    if bus not in visited:
                        visited.add(bus)
                        for s in routes[bus]:
                            if s == T: 
                                return res
                            t.append(s)
            queue = t
        return -1
```

本文链接：[https://www.jianshu.com/p/63d118245236](https://www.jianshu.com/p/63d118245236)
