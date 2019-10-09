 [题目链接](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串、双指针
***
 
给定一个字符串，请你找出其中不含有重复字符的 最长子串 的长度。
 
**示例1**
> 输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

**示例2**
>输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。

**示例3**
>输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。


#### 解题思路
***
 双指针：
指针l指在头，另一个指针r滑动遍历，在字典中记录遇到过的字符及下标
若指针r指向的字符没有出现过，记录并更新当前字串的长度
若出现过，l移到上次出现的坐标的下一位，不用比较当前的长度，因为当前的长度一定小于上一次的长度
直到r指向字符串最后一位



#### 代码实现
```
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        start = 0
        usedChar = {}
        max_len = 0
        for i in range(len(s)):
            if s[i] in usedChar and usedChar[s[i]] >= start:               
                start = usedChar[s[i]] + 1
            else:
                max_len = max(max_len, i-start+1)                              
            usedChar[s[i]] = i
        return max_len
        
```

本文链接：[https://www.jianshu.com/p/8efdc637f78d](https://www.jianshu.com/p/8efdc637f78d)
