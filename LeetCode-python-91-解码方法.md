 [题目链接](https://leetcode-cn.com/problems/decode-ways/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串、动态规划
***
 一条包含字母 A-Z 的消息通过以下方式进行了编码：

'A' -> 1
'B' -> 2
...
'Z' -> 26
给定一个只包含数字的非空字符串，请计算解码方法的总数。

 
**示例1**
> 输入: "12"
输出: 2
解释: 它可以解码为 "AB"（1 2）或者 "L"（12）。

**示例2**
>输入: "226"
输出: 3
解释: 它可以解码为 "BZ" (2 26), "VF" (22 6), 或者 "BBF" (2 2 6) 。

#### 解题思路
***
 dp[i]表示到第i-1位时解码的方法数
两种情况：
1.s[i-1]单独解码，方法数为dp[i-1]
2.s[i-2:i]拼接成双字符解码，若10<=s[i-2:i]<26，双字符合格，解码的方法数位dp[i-2]，否则为0
综合两种情况，得到状态转移矩阵：
dp[i] = dp[i-1] + (dp[i-2] if 双字符合格 else 0)

为什么dp[i]表示的使i-1位？
例如 216，在判断第二位‘1’时，i-2<0了，状态转移矩阵不能用了，故在前加一位，即dp[0]为1



#### 代码实现
```
class Solution(object):
    def numDecodings(self, s):
        """
        :type s: str
        :rtype: int
        """
        n = len(s)
        dp = [0]*(n+1)
        dp[0] = 1
        dp[1] = 1 if s[0]!='0' else 0
        for i in range(2,n+1):
            if s[i-1]!='0':
                dp[i] = dp[i-1]
             
            if 9< int(s[i-2:i])<27:
                dp[i] += dp[i-2]
            
        return dp[-1]
```

本文链接：[https://www.jianshu.com/p/d0905df9f65a](https://www.jianshu.com/p/d0905df9f65a)
