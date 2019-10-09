 [题目链接](https://leetcode-cn.com/problems/maximal-rectangle/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划
***
给定一个仅包含 0 和 1 的二维二进制矩阵，找出只包含 1 的最大矩形，并返回其面积。

 
**示例**
>输入:
[["1","0","1","0","0"],
  ["1","0","1","1","1"],
  ["1","1","1","1","1"],
  ["1","0","0","1","0"]]
输出: 6

#### 解题思路
***
矩形的面积等于$h \times w$，分别找出$h$和$w$即可
1. 计算$h$
row[i]是matrix的第i行，每行有n列，例如示例中，n=5
到达第$i$行时
当row[i][j] == '0' 时(其中$0\leq j<n$)，$h[j] = 0$
当row[i][j] == '1' 时(其中$0\leq j<n$)，$h[j] = row[i-1]的h[j] + 1$
例如，i = 2时，h = [3, 1, 3, 2, 2]，每一行都要求出h，一共求4组
2. 找到$w$
对于第2行的h，[3, 1, 3, 2, 2]，前三行所构成的矩形的面积可以是1，2，3，4，6，这是因为去了不同的$w$所造成的
当$w=4-2+1$是，面积等于6
[["x","x","x","x","x"],
  ["x","x","1","1","1"],
  ["x","x","1","1","1"],
  ["x","x","x","x","x"]
当$w=4-0+1$是，面积等于5
 [["x","x","x","x","x"],
  ["x","x","x","x","x"],
  ["1","1","1","1","1"],
  ["x","x","x","x","x"]
找出所有的$w$和$h$的组合，像极了[84题：柱状图中最大的矩形](https://www.jianshu.com/p/6f48a96b8d5a)

#### 代码实现
```
class Solution:
    def maximalRectangle(self, matrix: List[List[str]]) -> int:
        if not matrix or not matrix[0]:
            return 0
        n = len(matrix[0])
        height = [0] * (n+1)
        max_area = 0
        for row in matrix:
            # 计算h
            for i in range(n):
                height[i] = height[i]+1 if row[i]=='1' else 0
            # 找出所有h和w的组合 
            stack = [-1]
            for j in range(n + 1):
                while height[j] < height[stack[-1]]:
                    h = height[stack.pop()]
                    w = j - 1 - stack[-1]
                    max_area = max(max_area, h * w)                
                stack.append(j)            
        return max_area
```

本文链接：[https://www.jianshu.com/p/67cd5ba8802c](https://www.jianshu.com/p/67cd5ba8802c)
