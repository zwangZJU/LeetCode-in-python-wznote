 [题目链接](https://leetcode-cn.com/problems/rotate-image/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个 n × n 的二维矩阵表示一个图像。
将图像顺时针旋转 90 度。

说明：
你必须在原地旋转图像，这意味着你需要直接修改输入的二维矩阵。请不要使用另一个矩阵来旋转图像。
 
 
**示例1**
> 给定 matrix = 
[
  [1,2,3],
  [4,5,6],
  [7,8,9]
],
原地旋转输入矩阵，使其变为:
[
  [7,4,1],
  [8,5,2],
  [9,6,3]
]

**示例2**
> 给定 matrix =
[
  [ 5, 1, 9,11],
  [ 2, 4, 8,10],
  [13, 3, 6, 7],
  [15,14,12,16]
], 

原地旋转输入矩阵，使其变为:
[
  [15,13, 2, 5],
  [14, 3, 4, 1],
  [12, 6, 8, 9],
  [16, 7,10,11]
]

 
#### 解题思路
***
1. 转置，matrix[i][j]和matrix[j][i]互换
2. 行翻转 

#### 代码实现
```python
class Solution(object):
    def rotate(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: None Do not return anything, modify matrix in-place instead.
        """
        n = len(matrix[0])        
        # 矩阵转置
        for i in range(n):
            for j in range(i, n):
                matrix[j][i], matrix[i][j] = matrix[i][j], matrix[j][i] 
        
        # 行翻转
        for i in range(n):
            matrix[i].reverse()
```

本文链接：[https://www.jianshu.com/p/6bcdedc280ef](https://www.jianshu.com/p/6bcdedc280ef)
