[题目链接](https://leetcode-cn.com/problems/longest-palindromic-substring/)

难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。

 
**示例1**
> 输入: "babad"
输出: "bab"
注意: "aba" 也是一个有效答案。

**示例2**
> 输入: "cbbd"
输出: "bb"

#### 解题思路
***
遍历字符串，以每个字符和以每相邻两字符作为中心，搜索以其为中心的回文串长度，保存当前最长回文子串

中心扩展法判断是否符合回文要求



#### 代码实现
```
class Solution(object):
    def longestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        def expand(s, left, right):
            
            while left>=0 and right<len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return right-left-1
        start = 0
        end = 0
        for i in range(len(s)):
            len1 = expand(s, i, i)
            len2 = expand(s, i, i+1)
            max_len = max(len1, len2)
           
            if max_len > end - start:
                start = i - (max_len-1)/2
                
                end = i + max_len/2
        return s[start:end+1]
```

本文链接：[https://www.jianshu.com/p/faa70571e3d3](https://www.jianshu.com/p/faa70571e3d3)
