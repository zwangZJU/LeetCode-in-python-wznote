 [题目链接](https://leetcode-cn.com/problems/course-schedule/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  深度优先搜素、图、拓扑排序
***
 现在你总共有 n 门课需要选，记为 0 到 n-1。

在选修某些课程之前需要一些先修课程。 例如，想要学习课程 0 ，你需要先完成课程 1 ，我们用一个匹配来表示他们: [0,1]

给定课程总量以及它们的先决条件，判断是否可能完成所有课程的学习？

 
**示例1**
> 输入: 2, [[1,0]] 
输出: true
解释: 总共有 2 门课程。学习课程 1 之前，你需要完成课程 0。所以这是可能的。

**示例2**
>输入: 2, [[1,0],[0,1]]
输出: false
解释: 总共有 2 门课程。学习课程 1 之前，你需要先完成​课程 0；并且学习课程 0 之前，你还应先完成课程 1。这是不可能的。


#### 解题思路
***
 方法1：
每一次都删除没有入度的节点、看是否能删完

方法2：
找环，若有环就学不完



#### 代码实现
方法1
```python
class Solution(object):
    def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype: bool
        """
        d = {}
        for a,b in prerequisites:
            d[a] = d[a]+[b] if a in d else [b]
   
        courses = list(range(numCourses))
        t = len(courses)+1
       # 没有变化就跳出
        while len(courses)<t:
            t = len(courses)
            for c in courses:
                # 没有先修课程的课，即没有入度的节点
                if c not in d:     
                    # 学完就删除          
                    courses.remove(c)
                    for x in list(d.keys()):
                        if c in d[x]:
                            d[x].remove(c)
                            # 当x课的先修课程都学完了，就从字典删除它，它就成了没有入度的节点了
                            if d[x] == []:
                                d.pop(x)
             
        return courses == []
```
方法2：
```python
 class Solution(object):
    def canFinish(self, numCourses, prerequisites):
        """
        :type numCourses: int
        :type prerequisites: List[List[int]]
        :rtype: bool
        """
        graph = [[] for _ in range(numCourses)]
        visited = [0]*numCourses
        for k, v in prerequisites:
            graph[k].append(v)
        def dfs(i):
            if visited[i] == 1:
                return True
            if visited[i] == -1:
                return False
            visited[i] = -1
            for pre in graph[i]:
                if not dfs(pre):
                    return False
            visited[i] = 1
            return True
        for i in range(numCourses):
            if not dfs(i):
                return False
        return True
```

本文链接：[https://www.jianshu.com/p/4565fa200a62](https://www.jianshu.com/p/4565fa200a62)
