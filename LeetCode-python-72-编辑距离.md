 [题目链接](https://leetcode-cn.com/problems/edit-distance/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
 给定两个单词 word1 和 word2，计算出将 word1 转换成 word2 所使用的最少操作数 。

你可以对一个单词进行如下三种操作：

1. 插入一个字符
2. 删除一个字符
3. 替换一个字符


 
**示例1**
> 输入: word1 = "horse", word2 = "ros"
输出: 3
解释: 
horse -> rorse (将 'h' 替换为 'r')
rorse -> rose (删除 'r')
rose -> ros (删除 'e')

**示例2**
> 输入: word1 = "intention", word2 = "execution"
输出: 5
解释: 
intention -> inention (删除 't')
inention -> enention (将 'i' 替换为 'e')
enention -> exention (将 'n' 替换为 'x')
exention -> exection (将 'n' 替换为 'c')
exection -> execution (插入 'u')

#### 解题思路
***
 dp[i][j] 表示 word1 的前 i 个字母和 word2 的前 j 个字母之间的编辑距离

如果word1[i] = word2[j]，即两个子串的最后一个字母相同，就不用操作：
dp[i][j] = dp[i-1][j-1]

否则，在插入，替换和删除之中选择当前总编辑距离最小的一个，即
- 在dp[i][j-1]的基础上，在word1后插入一个和word2[j]一样的字符
- 在dp[i-1][j]的基础上，删除word1的第i个字符
- 在dp[i-1][j-1]的基础上，替换word1的最后一个字符和word2[j]相同

dp[i][j] = min(dp[i][j-1], dp[i-1][j], dp[i-1][j-1]) + 1



#### 代码实现
```python
class Solution(object):
    def minDistance(self, word1, word2):
        """
        :type word1: str
        :type word2: str
        :rtype: int
        """
        n = len(word1)+1
        m = len(word2)+1
        dp = [[0]*m for _ in range(n)]
        for i in range(n):
            for j in range(m):
                if j==0 or i==0:
                    dp[i][j] = max(j, i)
                elif word1[i-1]==word2[j-1]:
                    dp[i][j] = dp[i-1][j-1]
                else:
                    dp[i][j] = min([dp[i-1][j],dp[i][j-1],dp[i-1][j-1]])+1
        
        return dp[n-1][m-1]
        
```

本文链接：[https://www.jianshu.com/p/1d165cc7f185](https://www.jianshu.com/p/1d165cc7f185)
