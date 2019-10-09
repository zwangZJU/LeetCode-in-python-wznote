 [题目链接](https://leetcode-cn.com/problems/candy/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 老师想给孩子们分发糖果，有 N 个孩子站成了一条直线，老师会根据每个孩子的表现，预先给他们评分。

你需要按照以下要求，帮助老师给这些孩子分发糖果：
- 每个孩子至少分配到 1 个糖果。
- 相邻的孩子中，评分高的孩子必须获得更多的糖果。
那么这样下来，老师至少需要准备多少颗糖果呢？
 
**示例1**
> 输入: [1,0,2]
输出: 5
解释: 你可以分别给这三个孩子分发 2、1、2 颗糖果。

**示例2**
> 输入: [1,2,2]
输出: 4
解释: 你可以分别给这三个孩子分发 1、2、1 颗糖果。
     第三个孩子只得到 1 颗糖果，这已满足上述两个条件。

#### 解题思路
***
 1. 为了满足第一个条件（每个孩子至少分配到 1 个糖果），可以先给每个人发一个糖果
2. 评分高的孩子获得的糖果比左右相邻的孩子要多，可以这样考虑：先保证所有评分更高的孩子比左邻孩子糖果多，再实现所有评分更高的孩子比右邻孩子糖果多，为了用最少的糖果，多1个就好


#### 代码实现
```python
class Solution:
    def candy(self, ratings: List[int]) -> int:
        n = len(ratings)
        candies = [1]*n
        for i in range(1, n):
            if ratings[i]>ratings[i-1]:
                candies[i] = candies[i-1] + 1
        for i in range(n-2, -1, -1):
            if ratings[i]>ratings[i+1] and candies[i]<=candies[i+1] :
                candies[i] = candies[i+1]+1
        return sum(candies)
```

本文链接：[https://www.jianshu.com/p/a1ac709758ab](https://www.jianshu.com/p/a1ac709758ab)
