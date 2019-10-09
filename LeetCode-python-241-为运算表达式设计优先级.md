[题目链接](https://leetcode-cn.com/problems/different-ways-to-add-parentheses/description/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：分治
***
给定一个含有数字和运算符的字符串，为表达式添加括号，改变其运算优先级以求出不同的结果。你需要给出所有可能的组合的结果。有效的运算符号包含 +, - 以及 * 。

**示例1**
>输入: "2-1-1"
输出: [0, 2]
解释: 
((2-1)-1) = 0
(2-(1-1)) = 2

**示例2**
>输入: "2\*3-4\*5"
输出: [-34, -14, -10, -10, 10]
解释: 
(2\*(3-(4\*5))) = -34 
((2\*3)-(4\*5)) = -14 
((2\*(3-4))\*5) = -10 
(2\*((3-4)\*5)) = -10 
(((2\*3)-4)\*5) = 10

#### 解题思路：
***
- 对于题目指出的字符串，包括n个数字和n-1个运算符，选择第i个运算符，让其最后在运算
- 则运算符i的左边和右边可以分别独自进行运算，达到分治的效果
- 停止的条件为只剩边界的一个数字，或输入只有一个数字，返回该数字即可
#### 代码实现
```python
import re
import operator

class Solution:
    def diffWaysToCompute(self, input):
        items = re.split('(\D)', input)
        nums = list(map(int, items[::2]))
        ops = list(map({'+':operator.add, '-':operator.sub, '*':operator.mul}.get, items[1::2]))
        def calc(low, high):
            if low == high:
                return [nums[low]]
            return [ops[i](a, b)
               for i in range(low, high)
               for a in calc(low, i)
               for b in calc(i + 1, high)]
        return calc(0, len(nums)-1)
```

本文链接：[https://www.jianshu.com/p/0abc98c2db64](https://www.jianshu.com/p/0abc98c2db64)
