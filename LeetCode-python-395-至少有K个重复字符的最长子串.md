 [题目链接](https://leetcode-cn.com/problems/longest-substring-with-at-least-k-repeating-characters/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  回溯
***
 找到给定字符串（由小写字符组成）中的最长子串 T ， 要求 T 中的每一字符出现次数都不少于 k 。输出 T 的长度。

 
**示例1**
> 输入:
s = "aaabb", k = 3
输出:
3
最长子串为 "aaa" ，其中 'a' 重复了 3 次。

**示例2**
>输入:
s = "ababbc", k = 2
输出:
5
最长子串为 "ababb" ，其中 'a' 重复了 2 次， 'b' 重复了 3 次。

#### 解题思路
***
若一个字符出现的总次数小于k，它一定不在子串里，用它作为界限去分割
 



#### 代码实现
```python
class Solution(object):
    def longestSubstring(self, s, k):
        """
        :type s: str
        :type k: int
        :rtype: int
        """
        if len(s) < k:
            return 0
        c = min(set(s), key=s.count)
        if s.count(c) >= k:
            return len(s)
        return max(self.longestSubstring(t, k) for t in s.split(c))
```

本文链接：[https://www.jianshu.com/p/9e6f6ac86828](https://www.jianshu.com/p/9e6f6ac86828)
