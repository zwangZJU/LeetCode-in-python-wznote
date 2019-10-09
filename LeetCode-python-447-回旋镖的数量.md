 [题目链接](https://leetcode-cn.com/problems/number-of-boomerangs/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、数学
***
 给定平面上 n 对不同的点，“回旋镖” 是由点表示的元组 (i, j, k) ，其中 i 和 j 之间的距离和 i 和 k 之间的距离相等（需要考虑元组的顺序）。

找到所有回旋镖的数量。你可以假设 n 最大为 500，所有点的坐标在闭区间 [-10000, 10000] 中。
 
 
**示例**
> 输入:
[[0,0],[1,0],[2,0]]
输出:
2
解释:
两个回旋镖为 [[1,0],[0,0],[2,0]] 和 [[1,0],[2,0],[0,0]]

 
#### 解题思路
***
 以每个点作为第一个点进行考虑，计算到各个点之间的距离，相同距离点对的个数记录在字典中，k:v = 距离：个数
因为要考虑顺序，v个点的排列有v(v-1)种，累加即可



#### 代码实现
```python
class Solution:
    def numberOfBoomerangs(self, points: List[List[int]]) -> int:
        res = 0
        for a in points:
            dic = {}
            for b in points:
                d = (a[0]-b[0])**2 + (a[1]-b[1])**2
                dic[d] = 1 + dic.get(d, 0)
            for i in dic:
                res += dic[i] * (dic[i]-1)
        return res
```

本文链接：[https://www.jianshu.com/p/3907eacc7884](https://www.jianshu.com/p/3907eacc7884)
