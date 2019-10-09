 [题目链接](https://leetcode-cn.com/problems/insert-interval/)
难度： 困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组
***

**示例1**
>输入: intervals = [[1,3],[6,9]], newInterval = [2,5]
输出: [[1,5],[6,9]]

**示例2**
>输入: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
输出: [[1,2],[3,10],[12,16]]
解释: 这是因为新的区间 [4,8] 与 [3,5],[6,7],[8,10] 重叠。

#### 解题思路
***
需要插入的区间为[s,e]
原区间被分为三部分：
左边：区间的end小于s
右边：区间的start大于e
重叠：最小的start和最大的end

#### 代码实现
```
class Solution:
    def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
        s = newInterval[0]
        e = newInterval[1]
        left, right = [], []
        for inter in intervals:
            if s>inter[1]:
                left.append(inter)
            elif e<inter[0]:
                right.append(inter)
            else:
                s = min(s, inter[0])
                e = max(e, inter[1])
        return left + [[s, e]] + right  
```
