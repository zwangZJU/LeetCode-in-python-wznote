 [题目链接](https://leetcode-cn.com/problems/transpose-matrix/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个矩阵 A， 返回 A 的转置矩阵。

矩阵的转置是指将矩阵的主对角线翻转，交换矩阵的行索引与列索引。

 
**示例1**
> 输入：[[1,2,3],[4,5,6],[7,8,9]]
输出：[[1,4,7],[2,5,8],[3,6,9]]

**示例2**
>输入：[[1,2,3],[4,5,6]]
输出：[[1,4],[2,5],[3,6]]

#### 解题思路
***
 按列取元素放到新数组的行里



#### 代码实现
```python
class Solution:
    def transpose(self, A: List[List[int]]) -> List[List[int]]:
        r, c = len(A), len(A[0])
        res = [[] for _ in range(c)]
        for i in range(c):
            for j in range(r):               
                res[i].append(A[j][i])
        return res
```

本文链接：[https://www.jianshu.com/p/650189fa7a76](https://www.jianshu.com/p/650189fa7a76)
