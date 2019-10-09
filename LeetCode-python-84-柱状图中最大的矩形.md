 [题目链接](https://leetcode-cn.com/problems/largest-rectangle-in-histogram/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 数组
***
 给定 n 个非负整数，用来表示柱状图中各个柱子的高度。每个柱子彼此相邻，且宽度为 1 。

求在该柱状图中，能够勾勒出来的矩形的最大面积。

 
**示例**
>输入: [2,1,5,6,2,3]
输出: 10

#### 解题思路
***
用一个栈stack存储索引。
新的i在入栈前，先查看新的height[i]是否小于height[stack[-1]]：
若小于，i入栈
若不小于，弹出栈顶元素index，令height[index]为高，i为右边界，当前栈顶部为左边界。计算其面积并更新最大面积max_area。

#### 代码实现
```
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        n = len(heights)
        heights = heights+[0]
        stack = [-1]
        max_area = 0
        for i in range(n+1):
            while heights[i]<heights[stack[-1]]:
                h = heights[stack.pop()]
                w = i - stack[-1] - 1
                max_area = max(max_area, h*w)
            stack.append(i)
        return max_area
```

本文链接：[https://www.jianshu.com/p/6f48a96b8d5a](https://www.jianshu.com/p/6f48a96b8d5a)
