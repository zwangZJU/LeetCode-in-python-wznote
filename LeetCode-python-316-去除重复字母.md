 [题目链接](https://leetcode-cn.com/problems/remove-duplicate-letters/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  贪心、栈
***
 给定一个仅包含小写字母的字符串，去除字符串中重复的字母，使得每个字母只出现一次。需保证返回结果的字典序最小（要求不能打乱其他字符的相对位置）。

 
**示例1**
> 输入: "bcabc"
输出: "abc"
 
**示例2**
> 输入: "cbacdcbc"
输出: "acdb"

#### 解题思路
***
 遍历数组，一个一个考虑是否需要，若需要，就存入stack
遍历之前用collections.Counter统计每个字母的个数

当遍历到第i个字母s[i]时，首先s[i]的总个数减去1，再考虑这个字母要不要加入stack，加入之前，还要看已经加入的字母需不需要从stack中删除，例如bab,第一个b是要被删除的，因为b的字典序大于a,且a之后还有一个b，所以可以保留后一个b而删掉前一个b。那么，删除stack中最后一个字母stack[-1]的条件就是：
stack不空 且 stack[-1] > s[i] 且 s[i]不在stack中 且 stack[-1]的个数大于零

s[i]加入stack的条件就是:
s[i]不在stack中

#### 代码实现
```python
import collections
class Solution(object):
    def removeDuplicateLetters(self, s):
        """
        :type s: str
        :rtype: str
        """
        if not s:
            return s
        s = s.lower()
        dic = collections.Counter(s)
        stack = [s[0]]
        dic[s[0]] -= 1
        for i in range(1, len(s)):
            dic[s[i]] -= 1
            while stack and s[i] < stack[-1] and s[i] not in stack:
                if dic[stack[-1]] > 0:
                    stack.pop()
                else:
                    break
            if s[i] not in stack:
                stack.append(s[i])
                
        return ''.join(stack)
```

本文链接：[https://www.jianshu.com/p/e31aed2b4dc5](https://www.jianshu.com/p/e31aed2b4dc5)
