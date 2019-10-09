 [题目链接](https://leetcode-cn.com/problems/search-a-2d-matrix/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、二分查找
***
 编写一个高效的算法来判断 m x n 矩阵中，是否存在一个目标值。该矩阵具有如下特性：

每行中的整数从左到右按升序排列。
每行的第一个整数大于前一行的最后一个整数。
 
**示例1**
> 输入:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 3
输出: true

**示例2**
>输入:
matrix = [
  [1,   3,  5,  7],
  [10, 11, 16, 20],
  [23, 30, 34, 50]
]
target = 13
输出: false

#### 解题思路
***
用每一行的第一个元素与target相比
若当前元素小于target,向下一行
若当前元素大于target,遍历上一行的所有元素，看target是否存在于这一行

当然，二分查找才是更快的方式
有两种二分的方法：
1. 先行二分，确认target在该行后，再在该行中对列二分
2. 想象将二维矩阵的行按顺序拼接，是个有序的一维向量，标准二分，初始的时候left=0,right=n*m-1,mid=（left+right）/2,记得换回二维坐标去取元素值再和target比较就行


#### 代码实现
```python
class Solution(object):
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        if not matrix or not matrix[0]:
            return False
        m, n = len(matrix), len(matrix[0])
        for i in range(m):
            if i==m-1 or (i+1<m and matrix[i+1][0] > target):
                if i>=0:
                    return target in matrix[i]
                else:
                    return False
```

本文链接：[https://www.jianshu.com/p/bf83ba511b96](https://www.jianshu.com/p/bf83ba511b96)
