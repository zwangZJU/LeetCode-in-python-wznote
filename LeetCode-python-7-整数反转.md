 [题目链接](https://leetcode-cn.com/problems/reverse-integer/)
难度：简单       &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

 
**示例1**
> 输入: 123
输出: 321

**示例2**
>输入: -123
输出: -321

**示例3**
>输入: 120
输出: 21
 
#### 代码实现
```python
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        sign = 1 if x>0 else -1
        x = abs(x)
        
        stack = []
        while x>=1:
            stack.append(x%10)
            x = x / 10
        res = 0
        i = 0
        
        while stack:
       
            res += stack.pop() * 10**i
            i += 1
        return res*sign*(res<2**31)
```

本文链接：[https://www.jianshu.com/p/4252c8439c5b](https://www.jianshu.com/p/4252c8439c5b)
