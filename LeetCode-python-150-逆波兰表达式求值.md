 [题目链接](https://leetcode-cn.com/problems/evaluate-reverse-polish-notation/)

难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  栈
***
根据[逆波兰表示法](https://baike.baidu.com/item/%E9%80%86%E6%B3%A2%E5%85%B0%E5%BC%8F/128437)，求表达式的值。

有效的运算符包括 `+`, `-`, `*`, `/` 。每个运算对象可以是整数，也可以是另一个逆波兰表达式。

**说明：**

*   整数除法只保留整数部分。
*   给定逆波兰表达式总是有效的。换句话说，表达式总会得出有效数值且不存在除数为 0 的情况。

 
**示例1**
> 输入: ["2", "1", "+", "3", "*"]
输出: 9
解释: ((2 + 1) * 3) = 9

**示例2**
> 输入: ["4", "13", "5", "/", "+"]
输出: 6
解释: (4 + (13 / 5)) = 6

**示例3**
> 输入: ["10", "6", "9", "3", "+", "-11", "*", "/", "*", "17", "+", "5", "+"]
输出: 22
解释: 
  ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
#### 解题思路
***
 初始化一个空栈
若遇到数字，进栈
若遇到运算符，栈顶两个元素都出栈，进行运算，然后把结果入栈

此题的除法只保留整数部分
当除法的运算结果小于零时，若不是整除，为了保留整数部分，要+1


#### 代码实现
```
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        for token in tokens:
            if token not in ["+", "-", "*", "/"]:
                stack.append(int(token))              
            else:
                b, a = stack.pop(), stack.pop()
                if token == '+':
                    result = a + b
                elif token == '-':
                    result = a - b
                elif token == '*':
                    result = a * b
                elif token == '/':
                    result = a // b
                    result = result + 1 if result<0 and a%b!=0 else result                
                stack.append(result)
        return stack[0]
```

本文链接：[https://www.jianshu.com/p/6e15345d4758](https://www.jianshu.com/p/6e15345d4758)
