 [题目链接](https://leetcode-cn.com/problems/reverse-vowels-of-a-string/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 编写一个函数，以字符串作为输入，反转该字符串中的元音字母。

 
**示例1**
> 输入: "hello"
输出: "holle"

**示例2**
>输入: "leetcode"
输出: "leotcede"

#### 解题思路
***
双指针
一个指针p1从前往后走，另一个指针p2从后往前走
当两个指针都指向元音字母时，交换两元素位置
当p1未指向元音字母时，p1++
当p2未指向元音字母时，p2--

由于字符串是不可变类型，可以将字符串变成list，容易实现交换，最后用join拼接


#### 代码实现
```python
class Solution(object):
    def reverseVowels(self, s):
        vowels = {'a','e','i','o','u','A','E','I','O','U'}
        s = list(s)
        p1, p2 = 0, len(s) - 1
        while p1 < p2:
            if s[p1] in vowels and s[p2] in vowels:
                s[p1], s[p2] = s[p2], s[p1]
                p1 += 1
                p2 -= 1
            if s[p1] not in vowels:
                p1 += 1
            if s[p2] not in vowels:
                p2 -= 1
        return ''.join(s)

```

本文链接：[https://www.jianshu.com/p/b63cc8d950fd](https://www.jianshu.com/p/b63cc8d950fd)
