 [题目链接](https://leetcode-cn.com/problems/count-binary-substrings/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
给定一个字符串 s，计算具有相同数量0和1的非空(连续)子字符串的数量，并且这些子字符串中的所有0和所有1都是组合在一起的。

重复出现的子串要计算它们出现的次数。

 

 
**示例1**
> 输入: "00110011"
输出: 6
解释: 有6个子串具有相同数量的连续1和0：“0011”，“01”，“1100”，“10”，“0011” 和 “01”。
请注意，一些重复出现的子串要计算它们出现的次数。
另外，“00110011”不是有效的子串，因为所有的0（和1）没有组合在一起。

**示例2**
>输入: "10101"
输出: 4
解释: 有4个子串：“10”，“01”，“10”，“01”，它们具有相同数量的连续1和0。

#### 解题思路
***
 pre用来记录和当前字符不同的字符的个数
cur用来记录当前字符的个数
遍历字符串，当第i个字符和第i-1个字符一样时，cur++
反之，是0和1的交界处，计算pre和cur中更小的值，为有效子串的个数，有多长就有多少个，再将cur赋值给pre



#### 代码实现
```
class Solution(object):
    def countBinarySubstrings(self, s):
        """
        :type s: str
        :rtype: int
        """
        pre, cur, res = 0, 1, 0
      
        for i in range(1,len(s)):
            if s[i] == s[i-1]:
                cur += 1
            else:
                res += min(pre, cur)
                pre, cur = cur, 1
         
        return res + min(pre,cur)
            
```

本文链接：[https://www.jianshu.com/p/b720144945f3](https://www.jianshu.com/p/b720144945f3)
