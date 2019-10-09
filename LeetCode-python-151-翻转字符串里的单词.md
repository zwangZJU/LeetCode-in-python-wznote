 [题目链接](https://leetcode-cn.com/problems/reverse-words-in-a-string/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：字符串
***
给定一个字符串，逐个翻转字符串中的每个单词。

**示例1**
>输入: "the sky is blue"
输出: "blue is sky the"

**示例2**
>输入: "  hello world!  "
输出: "world! hello"
解释: 输入字符串可以在前面或者后面包含多余的空格，但是反转后的字符不能包括。

**示例3**
>输入: "a good   example"
输出: "example good a"
解释: 如果两个单词间有多余的空格，将反转后单词间的空格减少到只含一个。

#### 解题思路
***
将整个字符串翻转，再将翻转后字符串的每一个单词翻转

#### 代码实现
```
class Solution(object):
    def reverseWords(self, s):
        """
        :type s: str
        :rtype: str
        """       
        words = []
        for word in s[::-1].split():
            words.append(word[::-1])
        return ' '.join(words)
```

本文链接：[https://www.jianshu.com/p/d9db6fcf3367](https://www.jianshu.com/p/d9db6fcf3367)
