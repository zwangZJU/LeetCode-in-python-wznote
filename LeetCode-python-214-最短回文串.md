 [题目链接](https://leetcode-cn.com/problems/shortest-palindrome/
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 字符串 
***
 给定一个字符串 s，你可以通过在字符串前面添加字符将其转换为回文串。找到并返回可以用这种方式转换的最短回文串。

 
**示例1**
> 输入: "aacecaaa"
输出: "aaacecaaa"

**示例2**
>输入: "abcd"
输出: "dcbabcd"
#### 解题思路
***
 找到从头开始的最长回文串s[:i]，在头上加上s[i:]的翻转即可



#### 代码实现
方法1
```python
class Solution(object):
    def shortestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """
        def is_palindrome(s, i,j, n):
            if s[:i+1] == s[j:j+i+1][::-1]:
                return True
            return False
        n = len(s)        
        for i in range(n//2+1, -1, -1):            
            if is_palindrome(s, i, i+1, n):
                return s[2 * i+2:][::-1]+s
            elif is_palindrome(s, i, i, n):               
                return s[2 * i+1:][::-1]+s
```

方法2：
```python
 class Solution(object):
    def shortestPalindrome(self, s):
        """
        :type s: str
        :rtype: str
        """

        r = s[::-1]
        for i in range(len(s) + 1):
            if s.startswith(r[i:]):
                return r[:i] + s
```

本文链接：[https://www.jianshu.com/p/c2299d3c79d3](https://www.jianshu.com/p/c2299d3c79d3)
