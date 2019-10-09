 [题目链接](https://leetcode-cn.com/problems/spiral-matrix/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个包含 m x n 个元素的矩阵（m 行, n 列），请按照顺时针螺旋顺序，返回矩阵中的所有元素。

 
**示例1**
> 输入:
[
 [ 1, 2, 3 ],
 [ 4, 5, 6 ],
 [ 7, 8, 9 ]
]
输出: [1,2,3,6,9,8,7,4,5]

**示例2**
>输入:
[
  [1, 2, 3, 4],
  [5, 6, 7, 8],
  [9,10,11,12]
]
输出: [1,2,3,4,8,12,11,10,9,5,6,7]

#### 解题思路
***
 灵活运用pop()
先matrix.pop(0),取出上面一行
再pop matrix每一行的最后一个元素
再matrix.pop()，取出最下面一行
最后pop(0) matrix每一行的第一个元素

反复按顺序进行四个操作



#### 代码实现
```
class Solution(object):
    def spiralOrder(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: List[int]
        """
        res = []
        while matrix:
            res += matrix.pop(0)
            if matrix and matrix[0]:
                for m in matrix:
                     
                    res += [m.pop()]
            if matrix:
                res += matrix.pop()[::-1]
            t = []
            if matrix and matrix[0]:
                
                for m in matrix:
                     
                    t += [m.pop(0)]
                
                res += t[::-1]
        return res
```
