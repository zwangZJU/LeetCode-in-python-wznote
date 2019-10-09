 [题目链接](https://leetcode-cn.com/problems/car-pooling/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 贪心算法 
***
 假设你是一位顺风车司机，车上最初有 capacity 个空座位可以用来载客。由于道路的限制，车 只能 向一个方向行驶（也就是说，不允许掉头或改变方向，你可以将其想象为一个向量）。

这儿有一份行程计划表 trips[][]，其中 trips[i] = [num_passengers, start_location, end_location] 包含了你的第 i 次行程信息：

必须接送的乘客数量；
乘客的上车地点；
以及乘客的下车地点。
这些给出的地点位置是从你的 初始 出发位置向前行驶到这些地点所需的距离（它们一定在你的行驶方向上）。

请你根据给出的行程计划表和车子的座位数，来判断你的车是否可以顺利完成接送所用乘客的任务（当且仅当你可以在所有给定的行程中接送所有乘客时，返回 true，否则请返回 false）。
 
**示例1**
> 输入：trips = [[2,1,5],[3,3,7]], capacity = 4
输出：false

**示例2**
> 输入：trips = [[2,1,5],[3,3,7]], capacity = 5
输出：true

**示例3**
>输入：trips = [[2,1,5],[3,5,7]], capacity = 3
输出：true

**示例4**
>输入：trips = [[3,2,7],[3,7,9],[8,3,9]], capacity = 11
输出：true
#### 解题思路
***
[n,i,j]表示[人数，上车点，下车点]，将所有[n,i,j],改写成[i,n]和[j,-n],按上下车点从小到大排序

每次上车，从现有容量里减去乘客数
每次下车，从现有容量中加上乘客数
当容量小于零时，返回False
都不小于零，返回True



#### 代码实现
```python
class Solution:
    def carPooling(self, trips: List[List[int]], capacity: int) -> bool:
        for _, k in sorted([x for n, i, j in trips for x in ([i, n], [j, -n])]):
            capacity -= k
            if capacity<0:
                return False
        return True
```

本文链接：[https://www.jianshu.com/p/ce3616e51891](https://www.jianshu.com/p/ce3616e51891)
