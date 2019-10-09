 [题目链接](https://leetcode-cn.com/problems/isomorphic-strings/)
难度：简单        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给定两个字符串 s 和 t，判断它们是否是同构的。

如果 s 中的字符可以被替换得到 t ，那么这两个字符串是同构的。

所有出现的字符都必须用另一个字符替换，同时保留字符的顺序。两个字符不能映射到同一个字符上，但字符可以映射自己本身。
 

 
**示例1**
> 输入: s = "egg", t = "add"
输出: true

**示例2**
>输入: s = "foo", t = "bar"
输出: false

**示例3**
>输入: s = "paper", t = "title"
输出: true

#### 解题思路
***
见代码



#### 代码实现
```python
  class Solution(object):
    def isIsomorphic(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: bool
        """
        return len(set(zip(s,t))) == len(set(s)) == len(set(t))
```

本文链接：[https://www.jianshu.com/p/8c1ae686fd82](https://www.jianshu.com/p/8c1ae686fd82)
