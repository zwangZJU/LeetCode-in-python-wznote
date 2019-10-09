 [题目链接](https://leetcode-cn.com/problems/pascals-triangle-ii/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
给定一个非负索引 k，其中 k ≤ 33，返回杨辉三角的第 k 行。

 
**示例**
>输入: 3
输出: [1,3,3,1]

#### 解题思路
***
 杨辉三角的规律是某元素的值等于其肩上量元素值的和

有个巧妙的解法：
第三行为：1，3， 3， 1
第四行为：1， 4， 6， 4， 1
恰好有：
```
  0 1 3 3 1
+ 1 3 3 1 0
= 1 4 6 4 1
```
即分别首位添0，末位添0后对应位相加

一行一行递推到第rowIndex行

#### 代码实现
```python
class Solution(object):
    def getRow(self, rowIndex):
        """
        :type rowIndex: int
        :rtype: List[int]
        """
        row = [1]
        for _ in range(rowIndex):
            row = [x+y for x, y in zip([0]+row, row+[0])]
        return row
```

本文链接：[https://www.jianshu.com/p/049ffb6dd9a6](https://www.jianshu.com/p/049ffb6dd9a6)

 
