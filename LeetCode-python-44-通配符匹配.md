 [题目链接](https://leetcode-cn.com/problems/wildcard-matching/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
 给定一个字符串 (s) 和一个字符模式 (p) ，实现一个支持 '?' 和 '*' 的通配符匹配。

'?' 可以匹配任何单个字符。
'*' 可以匹配任意字符串（包括空字符串）。
两个字符串完全匹配才算匹配成功。

说明:
s 可能为空，且只包含从 a-z 的小写字母。
p 可能为空，且只包含从 a-z 的小写字母，以及字符 ? 和 *。

 
**示例1**
> 输入:
s = "aa"
p = "a"
输出: false
解释: "a" 无法匹配 "aa" 整个字符串。

**示例2**
> 输入:
s = "aa"
p = "*"
输出: true
解释: '*' 可以匹配任意字符串。

**示例3**
> 输入:
s = "cb"
p = "?a"
输出: false
解释: '?' 可以匹配 'c', 但第二个 'a' 无法匹配 'b'。

**示例4**
> 输入:
s = "adceb"
p = "*a*b"
输出: true
解释: 第一个 '*' 可以匹配空字符串, 第二个 '*' 可以匹配字符串 "dce".

**示例5**
> 输入:
s = "acdcb"
p = "a*c?b"
输入: false

#### 解题思路
***
状态转移方程：
如果p[i] == s[j] 或 p[i]=='?': dp[i+1][j+1] = dp[i][j]
如果 p[i] == '*': dp[i+1][j+1] = dp[i+1][j] or dp[i][j+1]  

dp的第一列要特殊处理，针对首字符为‘*’的情况



#### 代码实现
```python
class Solution(object):
    def isMatch(self, s, p):
        """
        :type s: str
        :type p: str
        :rtype: bool
        """
        m, n = len(s), len(p)
        dp = [[False] * (m+1) for _ in range(n+1)]
        dp[0][0] = True
        for i in range(n):
            if p[i] == '*':
                dp[i+1][0] = dp[i][0]
        for i in range(n):
            for j in range(m):
                if p[i] == s[j] or p[i]=='?':
                    dp[i+1][j+1] = dp[i][j]
                elif p[i] == '*':
                    dp[i+1][j+1] = dp[i+1][j] or dp[i][j+1]  
              
        return dp[-1][-1]
```

本文链接：[https://www.jianshu.com/p/882edd9a1c13](https://www.jianshu.com/p/882edd9a1c13)
