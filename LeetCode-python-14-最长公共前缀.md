[题目链接](https://leetcode-cn.com/problems/longest-common-prefix/)

难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组，字符串
***
 编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

 
**示例1**
> 输入: ["flower","flow","flight"]
输出: "fl"

**示例2**
> 输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。

#### 解题思路
***
 选择数组中的任意一个字符串作为模板
纵向比较，在第i次比较时，对比数组中剩余的每一个字符串的第i个字符与模板的第i个字符是否相同
若有一个不相同或者比较完了再或者剩余字符串长度不够了就返回第i位之前的子串



#### 代码实现
```
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        if not strs:
            return ''
        sample = strs[0]
        for i in range(len(sample)):
            for s in strs[1:]:
                if i<len(s) :
                    if s[i]!=sample[i]:
                        return sample[:i]
                else:
                    return s[:i]
        return sample
```

本文链接：[https://www.jianshu.com/p/31fd8235df50](https://www.jianshu.com/p/31fd8235df50)
