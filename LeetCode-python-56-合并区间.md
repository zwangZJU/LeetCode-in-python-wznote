 [题目链接](https://leetcode-cn.com/problems/merge-intervals/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给出一个区间的集合，请合并所有重叠的区间。

 
**示例1**
> 输入: [[1,3],[2,6],[8,10],[15,18]]
输出: [[1,6],[8,10],[15,18]]
解释: 区间 [1,3] 和 [2,6] 重叠, 将它们合并为 [1,6].

**示例2**
>输入: [[1,4],[4,5]]
输出: [[1,5]]
解释: 区间 [1,4] 和 [4,5] 可被视为重叠区间。

#### 解题思路
***
1. 按照start从小到大排列区间
2. 当前区间的start小于上一个区间的end，就合并区间，合并的方法是将上一个区间的end修改为当前区间和上一区间的最大值



#### 代码实现
```python
# Definition for an interval.
# class Interval(object):
#     def __init__(self, s=0, e=0):
#         self.start = s
#         self.end = e

class Solution(object):
    def merge(self, intervals):
        """
        :type intervals: List[Interval]
        :rtype: List[Interval]
        """
        if not intervals:
            return intervals
        intervals = sorted(intervals,  key=lambda x : x.start)
        res = [intervals[0]]
        for item in intervals[1:]:
            if item.start <= res[-1].end:
                res[-1].end = max(item.end, res[-1].end)
            else:
                res.append(item)
        return res
```

本文链接：[https://www.jianshu.com/p/5f0962779238](https://www.jianshu.com/p/5f0962779238)
