 [题目链接](https://leetcode-cn.com/problems/valid-palindrome/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。 

 
**示例1**
> 输入: "A man, a plan, a canal: Panama"
输出: true

**示例2**
>输入: "race a car"
输出: false

#### 解题思路
***
1. 去掉非数字和字母的字符
2. 字母转小写
3. 判断是否正序等于倒序 



#### 代码实现
```python
class Solution:
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        new_str = ''.join(filter(str.isalnum,s)).lower()
        return new_str[::-1] == new_str
```

本文链接：[https://www.jianshu.com/p/d74ff8e75687](https://www.jianshu.com/p/d74ff8e75687)

 
