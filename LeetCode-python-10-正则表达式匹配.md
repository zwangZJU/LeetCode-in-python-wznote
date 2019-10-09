 [题目链接](https://leetcode-cn.com/problems/regular-expression-matching/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划  
***
 给你一个字符串 s 和一个字符规律 p，请你来实现一个支持 '.' 和 '*' 的正则表达式匹配。

'.' 匹配任意单个字符
'*' 匹配零个或多个前面的那一个元素

所谓匹配，是要涵盖 整个 字符串 s的，而不是部分字符串。
 
**示例1**
> 输入:
s = "aa"
p = "a"
输出: false
解释: "a" 无法匹配 "aa" 整个字符串。

**示例2**
>输入:
s = "aa"
p = "a*"
输出: true
解释: 因为 '*' 代表可以匹配零个或多个前面的那一个元素, 在这里前面的元素就是 'a'。因此，字符串 "aa" 可被视为 'a' 重复了一次。

**示例3**
>输入:
s = "ab"
p = ".*"
输出: true
解释: ".*" 表示可匹配零个或多个（'*'）任意字符（'.'）。

**示例4**
>输入:
s = "aab"
p = "c*a*b"
输出: true
解释: 因为 '*' 表示零个或多个，这里 'c' 为 0 个, 'a' 被重复一次。因此可以匹配字符串 "aab"。

**示例5**
>输入:
s = "mississippi"
p = "mis*is*p*."
输出: false

#### 解题思路
***
直接上动态方程：

1. p[j] == s[i]:dp[i][j] = dp[i-1][j-1]
2. p[j] == ".":dp[i][j] = dp[i-1][j-1]
3. p[j] =="*":
3.1 p[j-1] != s[i]:dp[i][j] = dp[i][j-2]
3.2 p[i-1] == s[i] or p[i-1] == ".":
dp[i][j] = dp[i-1][j] // 匹配多个a
or dp[i][j] = dp[i][j-1] // 匹配单个a
or dp[i][j] = dp[i][j-2] // 匹配空字符

参考：https://leetcode-cn.com/problems/two-sum/solution/dong-tai-gui-hua-by-powcai/


#### 代码实现
```python
class Solution:
    def isMatch(self, s, p):
      
        s_len = len(s)
        p_len = len(p)
        dp = [[False] * (p_len + 1) for _ in range(s_len + 1)]
        
        dp[0][0] = True
        for i in range(p_len):
            if p[i] == "*" and dp[0][i - 1]:
                dp[0][i + 1] = True
        
        for i in range(s_len):
            for j in range(p_len):
                if p[j] == s[i] or p[j] == ".":
                    dp[i + 1][j + 1] = dp[i][j]
                elif p[j] == "*":
                    if p[j - 1] != s[i]:
                        dp[i + 1][j + 1] = dp[i + 1][j - 1]
                    if p[j-1] == s[i] or p[j-1] == ".":
                        dp[i+1][j+1] = (dp[i][j+1] or dp[i+1][j]   or  dp[i+1][j-1])
        
        return dp[-1][-1]
```

本文链接：[https://www.jianshu.com/p/f1e0bac8e4d3](https://www.jianshu.com/p/f1e0bac8e4d3)
