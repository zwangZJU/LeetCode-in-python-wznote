 [题目链接](https://leetcode-cn.com/problems/rectangle-overlap/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 
矩形以列表 [x1, y1, x2, y2] 的形式表示，其中 (x1, y1) 为左下角的坐标，(x2, y2) 是右上角的坐标。

如果相交的面积为正，则称两矩形重叠。需要明确的是，只在角或边接触的两个矩形不构成重叠。

给出两个矩形，判断它们是否重叠并返回结果。
 
**示例1**
> 输入：rec1 = [0,0,2,2], rec2 = [1,1,3,3]
输出：true

**示例2**
> 输入：rec1 = [0,0,1,1], rec2 = [1,0,2,1]
输出：false
#### 解题思路
***
 两个重叠的矩形一定有如下关系：
rec1的最左一定小于rec2的最右，rec2的最左一定小于rec1的最右
rec1的最下一定小于rec2的最上，rec2的最上一定小于rec1的最下



#### 代码实现
```python
class Solution(object):
    def isRectangleOverlap(self, rec1, rec2):
        """
        :type rec1: List[int]
        :type rec2: List[int]
        :rtype: bool
        """
        return rec1[0] < rec2[2] and rec2[0] < rec1[2] and rec1[1] < rec2[3] and rec2[1] < rec1[3]
```

本文链接：[https://www.jianshu.com/p/b33d9660b411](https://www.jianshu.com/p/b33d9660b411)
