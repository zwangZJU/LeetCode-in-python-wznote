 [题目链接](https://leetcode-cn.com/problems/word-pattern/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
给定一种规律 pattern 和一个字符串 str ，判断 str 是否遵循相同的规律。

这里的 遵循 指完全匹配，例如， pattern 里的每个字母和字符串 str 中的每个非空单词之间存在着双向连接的对应规律。

 
**示例1**
> 输入: pattern = "abba", str = "dog cat cat dog"
输出: true

**示例2**
>输入:pattern = "abba", str = "dog cat cat fish"
输出: false

**示例3**
>输入: pattern = "aaaa", str = "dog cat cat dog"
输出: false

**示例4**
>输入: pattern = "abba", str = "dog dog dog dog"
输出: false

#### 解题思路
***
和[205.同构字符串解法一致](https://www.jianshu.com/p/8c1ae686fd82)

#### 代码实现
```python
class Solution:
    def wordPattern(self, pattern, strs):
        """
        :type pattern: str
        :type str: str
        :rtype: bool
        """
        strs_list = strs.split()
        return len(strs_list) == len(pattern) and len(set(zip(pattern, strs_list))) == len(set(pattern)) == len(set(strs_list))
```

本文链接：[https://www.jianshu.com/p/45c533b0a120](https://www.jianshu.com/p/45c533b0a120)
