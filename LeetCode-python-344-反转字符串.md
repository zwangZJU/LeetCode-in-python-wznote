 [题目链接](https://leetcode-cn.com/problems/reverse-string/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 编写一个函数，其作用是将输入的字符串反转过来。输入字符串以字符数组 char[] 的形式给出。

不要给另外的数组分配额外的空间，你必须原地修改输入数组、使用 O(1) 的额外空间解决这一问题。

你可以假设数组中的所有字符都是 ASCII 码表中的可打印字符。

 
 
**示例1**
> 输入：["h","e","l","l","o"]
输出：["o","l","l","e","h"]

**示例2**
> 输入：["H","a","n","n","a","h"]
输出：["h","a","n","n","a","H"]
#### 解题思路
***
 双指针，start指向头，end指向尾，两个指针指向的元素交换，之后start加1，end减1，继续交换



#### 代码实现
```
class Solution(object):
    def reverseString(self, s):
        """
        :type s: List[str]
        :rtype: None Do not return anything, modify s in-place instead.
        """
        start = 0
        end = len(s)-1
        while start<end:
            s[start], s[end] = s[end], s[start]
            start += 1
            end -= 1
```

本文链接：[https://www.jianshu.com/p/eb95bd76090f](https://www.jianshu.com/p/eb95bd76090f)
