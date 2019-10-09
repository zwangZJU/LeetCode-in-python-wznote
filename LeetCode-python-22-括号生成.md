 [题目链接](https://leetcode-cn.com/problems/generate-parentheses/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  回溯
***
 给出 n 代表生成括号的对数，请你写出一个函数，使其能够生成所有可能的并且有效的括号组合。

 
**示例**
> 输入：3
输出：
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]

#### 解题思路
***
有n个左括号和n个右括号
用掉一个减一个
有效的括号需保证，剩余的左括号数<=剩余的右括号数，且数量都大于0 
若两者数量刚好都等于0，保存当前的括号组合


#### 代码实现
```
class Solution(object):
    def generateParenthesis(self, n):
        """
        :type n: int
        :rtype: List[str]
        """
        def generator(left, right, s, res):
            if left<0 or right<0 or left>right:
                return
            if left==0 and right==0:
                res.append(s)
                
            generator(left-1, right, s+'(', res)
            generator(left, right-1, s+')', res)
            
        res = []
        generator(n, n, '', res)
        return res
```

本文链接：[https://www.jianshu.com/p/38c83ba8d79e](https://www.jianshu.com/p/38c83ba8d79e)
