 [题目链接](https://leetcode-cn.com/problems/stone-game/description/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：贪心算法
***
给定字符串 s 和 t ，判断 s 是否为 t 的子序列。

你可以认为 s 和 t 中仅包含英文小写字母。字符串 t 可能会很长（长度 ~= 500,000），而 s 是个短字符串（长度 <=100）。

字符串的一个子序列是原始字符串删除一些（也可以不删除）字符而不改变剩余字符相对位置形成的新字符串。（例如，"ace"是"abcde"的一个子序列，而"aec"不是）。

**示例1**
s = "abc", t = "ahbgdc"
返回 true.

**示例2**
s = "axc", t = "ahbgdc"
返回 false.

 

#### 代码实现
```
class Solution:
    def isSubsequence(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        t = iter(t)
        return all(c in t for c in s)
```

本文链接：[https://www.jianshu.com/p/7d830c71a16b](https://www.jianshu.com/p/7d830c71a16b)
