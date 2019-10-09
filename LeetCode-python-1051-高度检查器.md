 [题目链接](https://leetcode-cn.com/problems/maximal-square/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组  
***
 学校在拍年度纪念照时，一般要求学生按照 非递减 的高度顺序排列。

请你返回至少有多少个学生没有站在正确位置数量。该人数指的是：能让所有学生以 非递减 高度排列的必要移动人数。
 
 
**示例**
> 输入：[1,1,4,2,1,3]
输出：3
解释：高度为 4、3 和最后一个 1 的学生，没有站在正确的位置

#### 解题思路
***
 方法1：排序，比较排序后和原顺序不同的位数

方法2：统计每个身高的个数，相当于桶排序的思想

#### 代码实现
方法1
```python
class Solution:
    def heightChecker(self, heights: List[int]) -> int:
        t = sorted(heights)
        res = 0
        for i in range(len(t)):
            if heights[i] != t[i]:
                res += 1
        return res
```

方法2
```python
class Solution:
    def heightChecker(self, heights: List[int]) -> int:
        c = [0] * 101
        n = len(heights)
        for i in range(n):
            c[heights[i]] += 1
        j = 1
        res = 0
        for i in range(n):
            while j<=100 and c[j]==0:
                j += 1
            if heights[i] != j:
                res += 1
            c[j] -= 1
        return res
```

本文链接：[https://www.jianshu.com/p/63485c2c2c17](https://www.jianshu.com/p/63485c2c2c17)
