 [题目链接](https://leetcode-cn.com/problems/combination-sum-iii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  深度优先搜索
***
 找出所有相加之和为 n 的 k 个数的组合。组合中只允许含有 1 - 9 的正整数，并且每种组合中不存在重复的数字。

 
**示例1**
> 输入: k = 3, n = 7
输出: [[1,2,4]]

**示例2**
> 输入: k = 3, n = 9
输出: [[1,2,6], [1,3,5], [2,3,4]]

#### 解题思路
***
 普通的深度优先搜索
用每一个数字都做一次第一位上的数，第i位上用大于第i-1位上数的所有数，结束条件为：
1. 刚好用够了k个数字
2. 总和超过了n
用了k个数字且和位n的组合保存下来

#### 代码实现
```python
class Solution(object):
    def combinationSum3(self, k, n):
        """
        :type k: int
        :type n: int
        :rtype: List[List[int]]
        """
        res = []
        def dfs(k, n, index, path):
            if k == 0 or n<0:
                if n == 0: res.append(path)
                return
            for i in range(index, 10):
                dfs(k-1, n-i, i+1, path+[i])
        dfs(k, n, 1, [])
        return res
```
本文链接：[https://www.jianshu.com/p/fe3dbb0bc908](https://www.jianshu.com/p/fe3dbb0bc908)

 
