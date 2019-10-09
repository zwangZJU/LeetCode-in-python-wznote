 [题目链接](https://leetcode-cn.com/problems/longest-valid-parentheses/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串、动态规划
***
 给定一个只包含 '(' 和 ')' 的字符串，找出最长的包含有效括号的子串的长度。

 
**示例1**
> 输入: "(()"
输出: 2
解释: 最长有效括号子串为 "()"

**示例2**
> 输入: ")()())"
输出: 4
解释: 最长有效括号子串为 "()()"

#### 解题思路
***
 方法1：（动态规划）
dp[i]表示以第i个字符结尾的有效括号的最长长度
对于（ ）（（ ））
i=4: dp = [0,2,0,0,2,0]
i=5: dp = [0,2,0,0,2,6]
dp[5] = 2 + dp[5-dp[5-1]-2]
解释：dp[i] 和dp[i-1]有关，还和dp[i-dp[i-1]-2]有关，没有第5位的‘）’时， 第2位的‘（’把0-4的字串分成了两端有效括号，但有了第5位的‘）’时，激活了这两段之间的连接，使之形成一整段有效括号

状态转移方程：
当s[i] == '(':dp[i] = 0
当s[i] == ')',并能找到前半个‘（’:
dp[i] = dp[i-dp[i-1]-2] + 2+ dp[i-1]



#### 代码实现
方法1：（动态规划）
```python
class Solution(object):
    def longestValidParentheses(self, s):
        """
        :type s: str
        :rtype: int
        """
        max_len = 0
        len_s = len(s)
        dp = [0]*len_s
        for i in range(1,len_s):
            if s[i] ==')':
                if i-dp[i-1]-1>=0 and s[i-dp[i-1]-1]=='(':                  
                    dp[i] = dp[i-dp[i-1]-2] + 2+ dp[i-1]
                    max_len = max(max_len, dp[i])            
        return max_len
```

本文链接：[https://www.jianshu.com/p/3cc0d3d17a25](https://www.jianshu.com/p/3cc0d3d17a25)
