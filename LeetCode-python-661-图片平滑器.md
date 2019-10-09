 [题目链接](https://leetcode-cn.com/problems/image-smoother/)
难度：简单        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组  
***
 包含整数的二维矩阵 M 表示一个图片的灰度。你需要设计一个平滑器来让每一个单元的灰度成为平均灰度 (向下舍入) ，平均灰度的计算是周围的8个单元和它本身的值求平均，如果周围的单元格不足八个，则尽可能多的利用它们。
 
 
**示例**
> 输入:
[[1,1,1],
 [1,0,1],
 [1,1,1]]
输出:
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]
解释:
对于点 (0,0), (0,2), (2,0), (2,2): 平均(3/4) = 平均(0.75) = 0
对于点 (0,1), (1,0), (1,2), (2,1): 平均(5/6) = 平均(0.83333333) = 0
对于点 (1,1): 平均(8/9) = 平均(0.88888889) = 0

 
#### 解题思路
***
 算就完事了



#### 代码实现
```python
class Solution(object):
    def imageSmoother(self, M):
        """
        :type M: List[List[int]]
        :rtype: List[List[int]]
        """
        d = [(-1,-1),(-1,0),(-1,1),(0,-1),(0,1),(1,-1),(1,0),(1,1)]
        n, m = len(M), len(M[0])
        res = [[0] * m for _ in M]
        for i in range(n):
            for j in range(m):
                sum = M[i][j]
                count = 1
                for dx,dy in d:                
                    if 0<=i+dx<n and 0<=j+dy<m:
                        sum += M[i+dx][j+dy]
                        count += 1
                res[i][j] = sum//count
        return res
```

本文链接：[https://www.jianshu.com/p/5eea43735f08](https://www.jianshu.com/p/5eea43735f08)
