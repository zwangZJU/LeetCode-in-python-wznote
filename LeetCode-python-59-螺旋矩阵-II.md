 [题目链接](https://leetcode-cn.com/problems/spiral-matrix-ii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个正整数 n，生成一个包含 1 到 n2 所有元素，且元素按顺时针顺序螺旋排列的正方形矩阵。


 
**示例**
> 输入: 3
输出:
[
 [ 1, 2, 3 ],
 [ 8, 9, 4 ],
 [ 7, 6, 5 ]
]
#### 解题思路
***
 按数字递增的方向，坐标值变化的方式为
上：dx=0, dy=1
右：dx=1, dy=0
下：dx=0,dy=-1
左：dx=-1,dy=0

每次拐弯：
dx都变为原来的dy
dy都变为原来的-dx

拐弯的条件：
matrix[x][y]已经有值，对于最外面一圈：matrix[x%n][y%n]有值



#### 代码实现
```
class Solution(object):
    def generateMatrix(self, n):
        """
        :type n: int
        :rtype: List[List[int]]
        """
        res = [[0]*n for _ in range(n)]
        i, j, di, dj = 0, 0, 0, 1
        for k in range(1, n*n+1):
            res[i][j] = k
            if res[(i+di)%n][(j+dj)%n]:
                di, dj = dj, -di
            i += di
            j += dj
        return res
```
