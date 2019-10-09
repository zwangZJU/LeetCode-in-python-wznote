 [题目链接](https://leetcode-cn.com/problems/greatest-common-divisor-of-strings/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串、数学
***
对于字符串 S 和 T，只有在 S = T + ... + T（T 与自身连接 1 次或多次）时，我们才认定 “T 能除尽 S”。

返回字符串 X，要求满足 X 能除尽 str1 且 X 能除尽 str2。

 
 
**示例1**
> 输入：str1 = "ABCABC", str2 = "ABC"
输出："ABC"

**示例2**
> 输入：str1 = "ABABAB", str2 = "ABAB"
输出："AB"

**示例3**
>输入：str1 = "LEET", str2 = "CODE"
输出：""

#### 解题思路
***
数学中求最大公约数的方法：辗转相除法
例如:找到25和10的最大公约数
25 / 10 = 2 余数 5
10 / 5 = 2 余 0
5就是最大公约数，此题同理 



#### 代码实现
```python
class Solution(object):
    def gcdOfStrings(self, str1, str2):
        """
        :type str1: str
        :type str2: str
        :rtype: str
        """
        l1, l2 = len(str1), len(str2)
        if l2 > l1:
            str1, str2 = str2, str1
            l1, l2 = l2, l1
        if l1 == l2:
            return str1 if str1==str2 else ''        
        f = l1%l2         
        if f == 0:            
            return str2 if str2*(l1//l2)==str1 else ''
        else:
            return self.gcdOfStrings(str2, str1[-f:])
```

本文链接：[https://www.jianshu.com/p/d0977fba8c3f](https://www.jianshu.com/p/d0977fba8c3f)
