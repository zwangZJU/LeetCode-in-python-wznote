 [题目链接](https://leetcode-cn.com/problems/minimum-number-of-arrows-to-burst-balloons/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  贪心算法
***
 在二维空间中有许多球形的气球。对于每个气球，提供的输入是水平方向上，气球直径的开始和结束坐标。由于它是水平的，所以y坐标并不重要，因此只要知道开始和结束的x坐标就足够了。开始坐标总是小于结束坐标。平面内最多存在104个气球。

一支弓箭可以沿着x轴从不同点完全垂直地射出。在坐标x处射出一支箭，若有一个气球的直径的开始和结束坐标为 xstart，xend， 且满足  xstart ≤ x ≤ xend，则该气球会被引爆。可以射出的弓箭的数量没有限制。 弓箭一旦被射出之后，可以无限地前进。我们想找到使得所有气球全部被引爆，所需的弓箭的最小数量。
 
**示例**
> 输入:
[[10,16], [2,8], [1,6], [7,12]]
输出:
2
解释:
对于该样例，我们可以在x = 6（射爆[2,8],[1,6]两个气球）和 x = 11（射爆另外两个气球）。

#### 解题思路
***
 按照区间的结束点从小到大排序
若第i个区间的起始点小于第i-1个区间的结束点，说明有重叠，可公用一支箭
反之，没有重叠，需要再用一支箭


#### 代码实现
```python
 class Solution(object):
    def findMinArrowShots(self, points):
        """
        :type points: List[List[int]]
        :rtype: int
        """
        if not points:
            return 0
        p = sorted(points, key=lambda x:x[1])
        res = 1
        end = p[0][1]
        for i in range(1,len(p)):
            if p[i][0] > end:
                res+=1
                end = p[i][1]
        return res
```

本文链接：[https://www.jianshu.com/p/382f6e86c5e4](https://www.jianshu.com/p/382f6e86c5e4)
