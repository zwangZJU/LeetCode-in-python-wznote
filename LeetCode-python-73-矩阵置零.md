 [题目链接](https://leetcode-cn.com/problems/set-matrix-zeroes/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个 *m* x *n* 的矩阵，如果一个元素为 0，则将其所在行和列的所有元素都设为 0。请使用原地算法。


 
**示例1**
> 输入: 
[
  [1,1,1],
  [1,0,1],
  [1,1,1]
]
输出: 
[
  [1,0,1],
  [0,0,0],
  [1,0,1]
]

**示例2**
>输入: 
[
  [0,1,2,0],
  [3,4,5,2],
  [1,3,1,5]
]
输出: 
[
  [0,0,0,0],
  [0,4,5,0],
  [0,3,1,0]
]

 
#### 解题思路
***
 遍历两遍
第一遍：遇到0时，将对应的行和列中不为0的元素全部替换成‘#’
第二遍：将所有的‘#’替换成0



#### 代码实现
```python
class Solution(object):
    def setZeroes(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: None Do not return anything, modify matrix in-place instead.
        """
        row, col = len(matrix), len(matrix[0])
        for i in range(row):
            for j in range(col):
                if matrix[i][j] == 0:
                    x = 0
                    while x<row:
                        if matrix[x][j]!=0:
                            matrix[x][j] = '#' 
                        x += 1
                    y = 0 
                    while y<col:
                        if matrix[i][y]!=0:
                            matrix[i][y] = '#' 
                        y += 1
        for i in range(row):
            for j in range(col):
                if matrix[i][j] == '#':
                    matrix[i][j] = 0 
```

本文链接：[https://www.jianshu.com/p/1dba5d8008ca](https://www.jianshu.com/p/1dba5d8008ca)
