 [题目链接](https://leetcode-cn.com/problems/word-break/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、字符串、动态规划
***
 给定一个非空字符串 s 和一个包含非空单词列表的字典 wordDict，判定 s 是否可以被空格拆分为一个或多个在字典中出现的单词。

说明：

拆分时可以重复使用字典中的单词。
你可以假设字典中没有重复的单词。

 
 
**示例1**
> 输入: s = "leetcode", wordDict = ["leet", "code"]
输出: true
解释: 返回 true 因为 "leetcode" 可以被拆分成 "leet code"。

 **示例2**
> 输入: s = "applepenapple", wordDict = ["apple", "pen"]
输出: true
解释: 返回 true 因为 "applepenapple" 可以被拆分成 "apple pen apple"。
     注意你可以重复使用字典中的单词。

  **示例3**
> 输入: s = "catsandog", wordDict = ["cats", "dog", "sand", "and", "cat"]
输出: false

#### 解题思路
***
 dp[i]表示到第i-1个字符时，是否为能被拆分为字典里的单词
状态转移矩阵：
dp[j] = dp[i] and s[i:j+1] in wordDict



#### 代码实现
```
class Solution(object):
    def wordBreak(self, s, wordDict):
        """
        :type s: str
        :type wordDict: List[str]
        :rtype: bool
        """
        n = len(s)
        dp = [True] + [False] * n
        for i in range(n):
            if dp[i]:
                for j in range(i, n):
                    if s[i:j+1] in wordDict:
                        dp[j+1] =True
        return dp[-1]
```

本文链接：[https://www.jianshu.com/p/471f11ef9368](https://www.jianshu.com/p/471f11ef9368)
