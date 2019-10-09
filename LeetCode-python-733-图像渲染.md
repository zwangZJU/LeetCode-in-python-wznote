 [题目链接](https://leetcode-cn.com/problems/flood-fill/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、深度优先搜索
***
 有一幅以二维整数数组表示的图画，每一个整数表示该图画的像素值大小，数值在 0 到 65535 之间。

给你一个坐标 (sr, sc) 表示图像渲染开始的像素值（行 ，列）和一个新的颜色值 newColor，让你重新上色这幅图像。

为了完成上色工作，从初始坐标开始，记录初始坐标的上下左右四个方向上像素值与初始坐标相同的相连像素点，接着再记录这四个方向上符合条件的像素点与他们对应四个方向上像素值与初始坐标相同的相连像素点，……，重复该过程。将所有有记录的像素点的颜色值改为新的颜色值。

最后返回经过上色渲染后的图像。
 
 
**示例**
> 输入: 
image = [[1,1,1],[1,1,0],[1,0,1]]
sr = 1, sc = 1, newColor = 2
输出: [[2,2,2],[2,2,0],[2,0,1]]
解析: 
在图像的正中间，(坐标(sr,sc)=(1,1)),
在路径上所有符合条件的像素点的颜色都被更改成2。
注意，右下角的像素没有更改为2，
因为它不是在上下左右四个方向上与初始点相连的像素点。
 
#### 解题思路
***
若起始点的颜色和newColor一致，直接返回原图
否则从这一点开始深度优先搜索，并修改颜色



#### 代码实现
```python
class Solution(object):
    def floodFill(self, image, sr, sc, newColor):
        """
        :type image: List[List[int]]
        :type sr: int
        :type sc: int
        :type newColor: int
        :rtype: List[List[int]]
        """
        self.n, self.m = len(image), len(image[0])
        if image[sr][sc] == newColor:
            return image
        def dfs(target, i, j):
            if 0<=i<self.n and 0<=j<self.m and image[i][j]==target:
                image[i][j] = newColor           
                dfs(target, i, j+1)
                dfs(target, i, j-1)
                dfs(target, i+1, j)
                dfs(target, i-1, j)
        dfs(image[sr][sc], sr, sc)
        return image
```

本文链接：[https://www.jianshu.com/p/32baa97f7c6b](https://www.jianshu.com/p/32baa97f7c6b)
