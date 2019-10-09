 [题目链接](https://leetcode-cn.com/problems/valid-parentheses/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串、栈
***
 给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

左括号必须用相同类型的右括号闭合。
左括号必须以正确的顺序闭合。
注意空字符串可被认为是有效字符串。

 
**示例1**
> 输入: "()"
输出: true

**示例2**
> 输入: "([)]"
输出: false

#### 解题思路
***
 遇到左括号入栈，遇到右括号栈顶元素出栈，比较两半括号是否是一对
成对的括号用字典存储



#### 代码实现
```
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        dic ={ '(':')', '[':']', '{':'}'}
       
        stack = []
        for c in s:
            if c in dic:
                stack.append(c)
            else:
                if stack:
                    top = stack.pop()
                    if c != dic[top]:
                        return False
                else:
                    return False
        return not stack
```

本文链接：[https://www.jianshu.com/p/8c8964c1c105](https://www.jianshu.com/p/8c8964c1c105)
