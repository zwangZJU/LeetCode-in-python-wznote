 [题目链接](https://leetcode-cn.com/problems/lexicographical-numbers/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、排序
***
 给定一个整数 n, 返回从 1 到 n 的字典顺序。

例如，

给定 n =1 3，返回 [1,10,11,12,13,2,3,4,5,6,7,8,9] 。

请尽可能的优化算法的时间复杂度和空间复杂度。 输入的数据 n 小于等于 5,000,000。
 

#### 代码实现
```python
class Solution:
    def lexicalOrder(self, n: int) -> List[int]:   
        return sorted(range(1, n+1), key=str)
```

本文链接：[https://www.jianshu.com/p/403be81c2905](https://www.jianshu.com/p/403be81c2905)
