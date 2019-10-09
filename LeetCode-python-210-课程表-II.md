 [题目链接](https://leetcode-cn.com/problems/course-schedule-ii/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 图 
***
 现在你总共有 n 门课需要选，记为 0 到 n-1。

在选修某些课程之前需要一些先修课程。 例如，想要学习课程 0 ，你需要先完成课程 1 ，我们用一个匹配来表示他们: [0,1]

给定课程总量以及它们的先决条件，返回你为了学完所有课程所安排的学习顺序。

可能会有多个正确的顺序，你只要返回一种就可以了。如果不可能完成所有课程，返回一个空数组。


**示例1**
> 输入: 2, [[1,0]] 
输出: [0,1]
解释: 总共有 2 门课程。要学习课程 1，你需要先完成课程 0。因此，正确的课程顺序为 [0,1] 。

**示例2**
>输入: 4, [[1,0],[2,0],[3,1],[3,2]]
输出: [0,1,2,3] or [0,2,1,3]
解释: 总共有 4 门课程。要学习课程 3，你应该先完成课程 1 和课程 2。并且课程 1 和课程 2 都应该排在课程 0 之后。
     因此，一个正确的课程顺序是 [0,1,2,3] 。另一个正确的排序是 [0,2,1,3] 。


#### 解题思路
***
遍历输入中的所有边，创建邻接表,out_degree[i]存储所有把第i节课作为预备课程的课，并用in_degree[i]存储结点i的入度。
将所有入度为0的边加入 res
执行以下操作直到 res中不再增加元素：
遍历res中的元素。不妨称为 N。对 N的所有邻接节点, 将其入度减去1。若任意结点的入度变为0，将其加入res。


#### 代码实现
```python
class Solution(object):
    def findOrder(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype: List[int]
        """
         
        in_degree = [0] * numCourses
        out_degree = [[] for _ in range(numCourses)] 
        for course, pre in prerequisites:
            in_degree[course] += 1
            out_degree[pre].append(course)
             
        res = []
        for i in range(numCourses):
            if in_degree[i] == 0:
                res.append(i)
        l = 0
        while l != len(res):
            x = res[l]
            l += 1
            for i in out_degree[x]:
                in_degree[i] -= 1
                if in_degree[i] == 0:
                    res.append(i)
        return res if l == numCourses else []
```

本文链接：[https://www.jianshu.com/p/1da55890d382](https://www.jianshu.com/p/1da55890d382)
