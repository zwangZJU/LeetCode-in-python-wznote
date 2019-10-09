 [题目链接](https://leetcode-cn.com/problems/score-of-parentheses/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串、栈
***
 给定一个平衡括号字符串 S，按下述规则计算该字符串的分数：

() 得 1 分。
AB 得 A + B 分，其中 A 和 B 是平衡括号字符串。
(A) 得 2 * A 分，其中 A 是平衡括号字符串。
 

 
**示例1**
> 输入： "()"
输出： 1

**示例2**
>输入： "(())"
输出： 2

**示例1**
>输入： "()()"
输出： 2

**示例1**
>输入： "()()"
输出： 2

#### 解题思路
***
 遇到‘（’,存到stack
遇到‘）’, 就要进行运算，若stack[-1]是‘（’，将最后stack[-1]修改为1；否则，不断pop出stack中的元素，是数字就累加，直到遇到‘（’，将累加的和乘2存在stack中



#### 代码实现
```python
class Solution(object):
    def scoreOfParentheses(self, S):
        """
        :type S: str
        :rtype: int
        """
        stack = []
        
        for c in S:
            if c == '(':
                stack.append('(')
            else:
                t = stack.pop()
                if t == '(':
                    stack.append(1)
                else:
                    cur_sum = 0
                    while t != '(':
                        cur_sum += t
                        if stack:
                            t = stack.pop()
                        else:                          
                            break
                    stack.append(cur_sum*2)
            
        return sum(stack)
```

本文链接：[https://www.jianshu.com/p/1d3811320c19](https://www.jianshu.com/p/1d3811320c19)
