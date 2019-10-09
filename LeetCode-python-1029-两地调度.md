 [题目链接](https://leetcode-cn.com/problems/two-city-scheduling/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  贪心算法
***
 公司计划面试 2N 人。第 i 人飞往 A 市的费用为 costs[i][0]，飞往 B 市的费用为 costs[i][1]。

返回将每个人都飞到某座城市的最低费用，要求每个城市都有 N 人抵达。

 
**示例**
> 输入：[[10,20],[30,200],[400,50],[30,20]]
输出：110
解释：
第一个人去 A 市，费用为 10。
第二个人去 A 市，费用为 30。
第三个人去 B 市，费用为 50。
第四个人去 B 市，费用为 20。

最低总费用为 10 + 30 + 50 + 20 = 110，每个城市都有一半的人在面试。

 
#### 解题思路
***
 方法1：
两地费用差的绝对值大的先安排

方法2：
两地费用求差，从小到大排序，前一半去a, 后一半去b



#### 代码实现
方法1：
```python
class Solution:
    def twoCitySchedCost(self, costs: List[List[int]]) -> int:
        costs = sorted(costs, key = lambda x: abs(x[0]-x[1]), reverse=True)    
        n = len(costs)//2  
        i, j = 0, 0
        res = 0
        for cost in costs:
            if cost[0]<cost[1] and i<n :
                res += cost[0]
                i += 1
            elif j<n:
                res += cost[1]
                j += 1
            else:
                res += cost[0]
        return res
```

方法2：
```python
class Solution:
    def twoCitySchedCost(self, costs: List[List[int]]) -> int:
        costs.sort(key=lambda x : (x[0]-x[1]))         
        n = len(costs)//2
        return sum([x[0] for x in costs[:n]]) + sum([x[1] for x in costs[n:]])
```

本文链接：[https://www.jianshu.com/p/aecc0931f672](https://www.jianshu.com/p/aecc0931f672)
