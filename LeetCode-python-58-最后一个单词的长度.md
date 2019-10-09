 [题目链接](https://leetcode-cn.com/problems/length-of-last-word/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给定一个仅包含大小写字母和空格 ' ' 的字符串，返回其最后一个单词的长度。

如果不存在最后一个单词，请返回 0 。

说明：一个单词是指由字母组成，但不包含任何空格的字符串。
 
 
**示例**
> 输入: "Hello World"
输出: 5

#### 解题思路
***
 去掉尾部的空格，从后往前数，返回到空格为止的长度



#### 代码实现
```
class Solution(object):
    def lengthOfLastWord(self, s):
        """
        :type s: str
        :rtype: int
        """
        s = s.strip()
        count = 0
        n = len(s)
        for i in range(n):
            if s[n-i-1] == ' ':
                return count
            else:
                count += 1
        return count
```
