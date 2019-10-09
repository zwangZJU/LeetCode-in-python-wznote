 [题目链接](https://leetcode-cn.com/problems/find-the-difference/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
给定两个字符串 s 和 t，它们只包含小写字母。

字符串 t 由字符串 s 随机重排，然后在随机位置添加一个字母。

请找出在 t 中被添加的字母。 

 
**示例**
> 输入：
s = "abcd"
t = "abcde"
输出：
e
解释：
'e' 是那个被添加的字母。

#### 解题思路
***
只添加了一个字符，问题可以看做在s+t中只出现一次的字符或者出现奇数次的字符
同[136.只出现一次的数字](https://www.jianshu.com/p/f3c2a20da915)

#### 代码实现
```python
class Solution(object):
    def findTheDifference(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: str
        """
        res = 0
        for c in s+t:
            res ^= ord(c)
        return chr(res)
```

本文链接：[https://www.jianshu.com/p/2cf5e67b6fe7](https://www.jianshu.com/p/2cf5e67b6fe7)
