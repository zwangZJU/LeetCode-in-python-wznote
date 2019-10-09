 [题目链接](https://leetcode-cn.com/problems/palindrome-partitioning/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：字符串
***

**示例**
>输入: "aab"
输出: [ ["aa","b"],["a","a","b"]]

#### 解题思路
***
深度优先搜索
结束条件：搜索完整个字符串
符合条件的子串：原本的子串和该子串逆序后相同，为回文子串。

#### 代码实现
```
class Solution(object):
    def partition(self, s):
        """
        :type s: str
        :rtype: List[List[str]]
        """
        res = []
        def dfs(s, path):
            if not s:
                res.append(path)
                return
            for i in range(1,len(s)+1):
                if s[:i] == s[:i][::-1]:
                    dfs(s[i:], path+[s[:i]])
        dfs(s, [])
        return res
```

本文链接：[https://www.jianshu.com/p/ac74819c14e7](https://www.jianshu.com/p/ac74819c14e7)
