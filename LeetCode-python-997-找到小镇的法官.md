 [题目链接](https://leetcode-cn.com/problems/maximal-square/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、图
***
 在一个小镇里，按从 1 到 N 标记了 N 个人。传言称，这些人中有一个是小镇上的秘密法官。

如果小镇的法官真的存在，那么：

小镇的法官不相信任何人。
每个人（除了小镇法官外）都信任小镇的法官。
只有一个人同时满足属性 1 和属性 2 。
给定数组 trust，该数组由信任对 trust[i] = [a, b] 组成，表示标记为 a 的人信任标记为 b 的人。

如果小镇存在秘密法官并且可以确定他的身份，请返回该法官的标记。否则，返回 -1。
 

 
**示例1**
> 输入：N = 2, trust = [[1,2]]
输出：2

**示例2**
>输入：N = 3, trust = [[1,3],[2,3]]
输出：3

**示例3**
>输入：N = 3, trust = [[1,3],[2,3],[3,1]]
输出：-1

**示例4**
>输入：N = 3, trust = [[1,2],[2,3]]
输出：-1

**示例5**
>输入：N = 4, trust = [[1,3],[1,4],[2,3],[2,4],[4,3]]
输出：3

#### 解题思路
***
 从图的角度看，只有法官的出度为0，入度为N-1



#### 代码实现
```python
class Solution(object):
    def findJudge(self, N, trust):
        """
        :type N: int
        :type trust: List[List[int]]
        :rtype: int
        """
        count = [0] * (N+1)
        for i, j in trust:
            count[i] -= 1
            count[j] += 1
         
        for i in range(1,N+1):
            if count[i] == N-1:
                return i
        return -1
```

本文链接：[https://www.jianshu.com/p/3e64ae138955](https://www.jianshu.com/p/3e64ae138955)
