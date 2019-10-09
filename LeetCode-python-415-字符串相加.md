 [题目链接](https://leetcode-cn.com/problems/add-strings/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给定两个字符串形式的非负整数 num1 和num2 ，计算它们的和。

注意：

num1 和num2 的长度都小于 5100.
num1 和num2 都只包含数字 0-9.
num1 和num2 都不包含任何前导零。
你不能使用任何內建 BigInteger 库， 也不能直接将输入的字符串转换为整数形式。

 
#### 解题思路
***
 逐位相加，记得进位



#### 代码实现
```python
class Solution:
    def addStrings(self, num1: str, num2: str) -> str:
        n1, n2 = len(num1), len(num2)
        n = max(n1, n2)
        num1, num2 = num1[::-1], num2[::-1]
      
        carry, res = 0, ''
        for i in range(n):
            a = int(num1[i]) if i<n1 else 0
            b = int(num2[i]) if i<n2 else 0
            sum = a+carry +b  
            carry = sum // 10
            res = str(sum % 10) + res
            
    
        return str(carry) + res if carry else res
```

本文链接：[https://www.jianshu.com/p/a74867a272ab](https://www.jianshu.com/p/a74867a272ab)
