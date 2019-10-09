 [题目链接](https://leetcode-cn.com/problems/decode-string/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  栈
***
 给定一个经过编码的字符串，返回它解码后的字符串。

编码规则为: k[encoded_string]，表示其中方括号内部的 encoded_string 正好重复 k 次。注意 k 保证为正整数。

你可以认为输入字符串总是有效的；输入字符串中没有额外的空格，且输入的方括号总是符合格式要求的。

此外，你可以认为原始数据不包含数字，所有的数字只表示重复的次数 k ，例如不会出现像 3a 或 2[4] 的输入。
 
**示例**
> s = "3[a]2[bc]", 返回 "aaabcbc".
s = "3[a2[c]]", 返回 "accaccacc".
s = "2[abc]3[cd]ef", 返回 "abcabccdcdcdef".

 
#### 解题思路
***
用[s, k]的list存储括号内部的数字及重复的次数，以该结构存入stack，已解决括号嵌套的问题
每次遇到数字的时候，开始记录数字，遇到’['的时候结束记录数字，将['',int(num)]存入stack
 每次遇到‘]'再解码，解码的结果存储在上一层括号的s处
stack初始化为[['',1]]，相当于在整体的外面加一层括号
最后返回stack[0][0]*stack[0][1]



#### 代码实现
```python
class Solution:
    def decodeString(self, s: str) -> str:
        stack = [['', 1]]
        num = ''
        for c in s:
            if c.isdigit():
                num += c
            elif c == '[':
                stack.append(['', int(num)])
                num = ''
            elif c == ']':
                subs, k = stack.pop()
                stack[-1][0] += subs*k
            else:
                stack[-1][0] += c
        return stack[0][0]*stack[0][1]
```

本文链接：[https://www.jianshu.com/p/dcb883e3c0f2](https://www.jianshu.com/p/dcb883e3c0f2)
