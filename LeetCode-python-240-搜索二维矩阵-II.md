 [题目链接](https://leetcode-cn.com/problems/search-a-2d-matrix-ii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 编写一个高效的算法来搜索 m x n 矩阵 matrix 中的一个目标值 target。该矩阵具有以下特性：
- 每行的元素从左到右升序排列。
- 每列的元素从上到下升序排列

 
**示例**
> 现有矩阵 matrix 如下：
[
  [1,   4,  7, 11, 15],
  [2,   5,  8, 12, 19],
  [3,   6,  9, 16, 22],
  [10, 13, 14, 17, 24],
  [18, 21, 23, 26, 30]
]
给定 target = 5，返回 true。
给定 target = 20，返回 false。

#### 解题思路
***
逐行搜索，从最后一列开始比较，即起始点为右上角的元素
如果target小于该元素，往左走，如果target大于该元素，往下走，重复此步骤
若走出边界还未找到，返回false；若找到，返回true



#### 代码实现
```python
 class Solution(object):
    def searchMatrix(self, matrix, target):
        """
        :type matrix: List[List[int]]
        :type target: int
        :rtype: bool
        """
        if not matrix:
            return False
        n = len(matrix)
        m = len(matrix[0])
        i = 0
        j = m-1
        while i<n and j>=0:
            if matrix[i][j] > target:
                j -= 1
            elif matrix[i][j] < target:
                i += 1
            else:
                return True
        return False
```

本文链接：[https://www.jianshu.com/p/7c20238ee0cd](https://www.jianshu.com/p/7c20238ee0cd)
