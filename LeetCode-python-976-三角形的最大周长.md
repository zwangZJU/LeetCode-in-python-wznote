[题目链接](https://leetcode-cn.com/problems/largest-perimeter-triangle/)

难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学
***
 给定由一些正数（代表长度）组成的数组 A，返回由其中三个长度组成的、面积不为零的三角形的最大周长。

如果不能形成任何面积不为零的三角形，返回 0。

 
**示例1**
> 输入：[2,1,2]
输出：5

**示例2**
>输入：[1,2,1]
输出：0

**示例3**
>输入：[3,2,3,4]
输出：10

**示例4**
>输入：[3,6,2,3]
输出：8

#### 解题思路
***
 先排序，最大的周长最有可能在更长的边长的组合下产生
倒序遍历
筛选条件为两边之和大于第三边，确切的说是两小边之和大于第三个大边


#### 代码实现
```python
class Solution:
    def largestPerimeter(self, A: List[int]) -> int:
        a = sorted(A)
        for i in range(len(a)-3,-1,-1):
            cur = a[i:i+3]
            if cur[0]+cur[1]>cur[2]:
                return sum(cur)
        return 0
```

本文链接：[https://www.jianshu.com/p/8f98dde7295e](https://www.jianshu.com/p/8f98dde7295e)
