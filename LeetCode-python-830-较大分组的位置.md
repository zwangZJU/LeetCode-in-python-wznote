 [题目链接](https://leetcode-cn.com/problems/positions-of-large-groups/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  双指针
***
 在一个由小写字母构成的字符串 S 中，包含由一些连续的相同字符所构成的分组。

例如，在字符串 S = "abbxxxxzyy" 中，就含有 "a", "bb", "xxxx", "z" 和 "yy" 这样的一些分组。

我们称所有包含大于或等于三个连续字符的分组为较大分组。找到每一个较大分组的起始和终止位置。

最终结果按照字典顺序输出。
 
**示例1**
> 输入: "abbxxxxzzy"
输出: [[3,6]]
解释: "xxxx" 是一个起始于 3 且终止于 6 的较大分组。

**示例2**
> 输入: "abc"
输出: []
解释: "a","b" 和 "c" 均不是符合要求的较大分组。

**示例3**
> 输入: "abcdddeeeeaabbbcd"
输出: [[3,5],[6,9],[12,14]]


#### 解题思路
***
 当S[i]不等于S[i-1]时，求分组的长度i-start，之后将start更新为i



#### 代码实现
```python
class Solution(object):
    def largeGroupPositions(self, S):
        """
        :type S: str
        :rtype: List[List[int]]
        """
        start, n, res = 0, len(S), []
        for i in range(1,n):
            if S[i] != S[i-1]:
                if i-start>=3:
                    res.append([start, i-1])
                start = i
        if n-1-start>=2:
            res.append([start, n-1])
        return res
```

本文链接：[https://www.jianshu.com/p/9baa918e7768](https://www.jianshu.com/p/9baa918e7768)
