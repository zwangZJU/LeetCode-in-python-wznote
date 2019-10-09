 [题目链接](https://leetcode-cn.com/problems/friend-circles/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、深度优先搜索
***
 班上有 N 名学生。其中有些人是朋友，有些则不是。他们的友谊具有是传递性。如果已知 A 是 B 的朋友，B 是 C 的朋友，那么我们可以认为 A 也是 C 的朋友。所谓的朋友圈，是指所有朋友的集合。

给定一个 N * N 的矩阵 M，表示班级中学生之间的朋友关系。如果M[i][j] = 1，表示已知第 i 个和 j 个学生互为朋友关系，否则为不知道。你必须输出所有学生中的已知的朋友圈总数。
 
 
**示例1**
> 输入: 
[[1,1,0],
 [1,1,0],
 [0,0,1]]
输出: 2 
说明：已知学生0和学生1互为朋友，他们在一个朋友圈。
第2个学生自己在一个朋友圈。所以返回2。

**示例2**
> 输入: 
[[1,1,0],
 [1,1,1],
 [0,1,1]]
输出: 1
说明：已知学生0和学生1互为朋友，学生1和学生2互为朋友，所以学生0和学生2也是朋友，所以他们三个在一个朋友圈，返回1。
 
#### 解题思路
***
 n = len(M) 说明只有n个人
从第1个人开始，找他的所有朋友，再找他所有朋友的所有朋友，再找。。。以此类推，直到找不到，这就找出了一个朋友圈
找过的人都要记在集合中，以后就不再重复寻找



#### 代码实现
```
class Solution(object):
    def findCircleNum(self, M):
        """
        :type M: List[List[int]]
        :rtype: int
        """
        res = 0
        seen = set()
        def dfs(row):
            for col, val in enumerate(M[row]):
                if val and col not in seen:
                    seen.add(col)
                    dfs(col)
        for i in range(len(M)):
            if i not in seen:
                dfs(i)
                res += 1
        return res
```

本文链接：[https://www.jianshu.com/p/ac5f29945438](https://www.jianshu.com/p/ac5f29945438)
