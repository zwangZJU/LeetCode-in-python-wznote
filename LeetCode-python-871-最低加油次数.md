 [题目链接](https://leetcode-cn.com/problems/minimum-number-of-refueling-stops/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  贪心算法、动态规划
***
 汽车从起点出发驶向目的地，该目的地位于出发位置东面 target 英里处。

沿途有加油站，每个 station[i] 代表一个加油站，它位于出发位置东面 station[i][0] 英里处，并且有 station[i][1] 升汽油。

假设汽车油箱的容量是无限的，其中最初有 startFuel 升燃料。它每行驶 1 英里就会用掉 1 升汽油。

当汽车到达加油站时，它可能停下来加油，将所有汽油从加油站转移到汽车中。

为了到达目的地，汽车所必要的最低加油次数是多少？如果无法到达目的地，则返回 -1 。

注意：如果汽车到达加油站时剩余燃料为 0，它仍然可以在那里加油。如果汽车到达目的地时剩余燃料为 0，仍然认为它已经到达目的地。
  
**示例1**
> 输入：target = 1, startFuel = 1, stations = []
输出：0
解释：我们可以在不加油的情况下到达目的地。

**示例2**
>输入：target = 100, startFuel = 1, stations = [[10,100]]
输出：-1
解释：我们无法抵达目的地，甚至无法到达第一个加油站。

**示例3**
>输入：target = 100, startFuel = 10, stations = [[10,60],[20,30],[30,30],[60,40]]
输出：2
解释：
我们出发时有 10 升燃料。
我们开车来到距起点 10 英里处的加油站，消耗 10 升燃料。将汽油从 0 升加到 60 升。
然后，我们从 10 英里处的加油站开到 60 英里处的加油站（消耗 50 升燃料），
并将汽油从 10 升加到 50 升。然后我们开车抵达目的地。
我们沿途在1两个加油站停靠，所以返回 2 。

 
#### 解题思路
***
 方法1（贪心算法）：
一直走，如果在到达下一站前没油了，再想着去加油：贪婪地选择油量最大的加油站去加

方法2（动态规划）：
把 “到达target最少要加几次油”转化为“加k次油最多能跑多远”
dp[i]表示加i次油能跑的最远的距离
若加k次油能跑到第i个加油站，则dp[k+1] = max(dp[k+1], dp[k]+第i个加油站的油量)
最后从头遍历dp，找到第一个大于等于target的数，返回其下标

#### 代码实现
方法1（贪心算法）：
```python
import heapq
class Solution(object):
    def minRefuelStops(self, target, startFuel, stations):
        """
        :type target: int
        :type startFuel: int
        :type stations: List[List[int]]
        :rtype: int
        """
        hp = []
        res = pre = 0
        tank = startFuel
        stations.append([target,0])
        for loc, gas in stations:             
            tank -= loc - pre
            while tank<0:
                if not hp:
                    return -1
                tank += -heapq.heappop(hp)
                res += 1
            heapq.heappush(hp, -gas)
            pre = loc
        return res
```

方法2（动态规划）：
```python
class Solution(object):
    def minRefuelStops(self, target, startFuel, stations):
        """
        :type target: int
        :type startFuel: int
        :type stations: List[List[int]]
        :rtype: int
        """
        dp = [startFuel] + [0]*len(stations)
        for i, (loc, gas) in enumerate(stations):
            for j in range(i, -1, -1):
                if dp[j] >= loc:
                    dp[j+1] = max(dp[j+1], dp[j]+gas)
        for i, d in enumerate(dp):
            if d>=target:
                return i
        return -1
```

本文链接：[https://www.jianshu.com/p/b823b1f87179](https://www.jianshu.com/p/b823b1f87179)
