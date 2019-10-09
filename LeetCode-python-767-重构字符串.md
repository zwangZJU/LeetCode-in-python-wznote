 [题目链接](https://leetcode-cn.com/problems/reorganize-string/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给定一个字符串S，检查是否能重新排布其中的字母，使得两相邻的字符不同。

若可行，输出任意可行的结果。若不可行，返回空字符串。

 
**示例1**
> 输入: S = "aab"
输出: "aba"

**示例2**
> 输入: S = "aaab"
输出: ""

#### 解题思路
***
 先统计所有字符各自的数量，按数量从大到小排列字符
若某个字符c的数量k超过总字符数的一半，必然不能达到要求，直接返回‘’
否则，将k个c存入stack中
这样就把所有相同的字符放在了相邻的位置
最后把stack中后一半字符放在偶数位，把前一半字符放在奇数位，构成新的字符串返回




#### 代码实现
```python
class Solution(object):
    def reorganizeString(self, S):
        """
        :type S: str
        :rtype: str
        """
        n = len(S)
        stack = []
        for k, c in sorted((S.count(x),x) for x in set(S)):
            if k>(n+1)/2:
                return ''
            stack.extend([c]*k)
        res = [None]*n
        res[::2], res[1::2] =  stack[n//2:], stack[:n//2]
        return ''.join(res)
```

本文链接：[https://www.jianshu.com/p/83e4902f1160](https://www.jianshu.com/p/83e4902f1160)
