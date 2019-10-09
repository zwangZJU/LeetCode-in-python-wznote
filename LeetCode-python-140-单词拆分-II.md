 [题目链接](https://leetcode-cn.com/problems/word-break-ii/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
给定一个非空字符串 s 和一个包含非空单词列表的字典 wordDict，在字符串中增加空格来构建一个句子，使得句子中所有的单词都在词典中。返回所有这些可能的句子。

说明：
分隔时可以重复使用字典中的单词。
你可以假设字典中没有重复的单词。

 
**示例1**
> 输入:
s = "catsanddog"
wordDict = ["cat", "cats", "and", "sand", "dog"]
输出:
[
  "cats and dog",
  "cat sand dog"
]

**示例2**
>输入:
s = "pineapplepenapple"
wordDict = ["apple", "pen", "applepen", "pine", "pineapple"]
输出:
[
  "pine apple pen apple",
  "pineapple pen apple",
  "pine applepen apple"
]
解释: 注意你可以重复使用字典中的单词。

**示例3**
>输入:
s = "catsandog"
wordDict = ["cats", "dog", "sand", "and", "cat"]
输出:
[]

#### 解题思路
***
1. 遍历wordDict中的每一个word，查看字符串s是否是由word开头的，即word是否是s的前缀
2. 若是，就将改word存储在结果中，并将s去掉这个word前缀，再进行第1步

如示例1
s = "catsanddog"
wordDict = ["cat", "cats", "and", "sand", "dog"]

s是以cat开头的，将cat存储再result中，把s变为sanddog，再遍历wordDict，发现sand是新s的前缀，再将sand存储。。。

可以发现，多次调用了第1步，程序中可以递归地调用，而对于下面这种情况：
s = "catsanddog"
wordDict = ["cat", "c", "at", "and", "s", "sand", "dog"]

前缀为‘cat’ 或者‘c at’对应的都是后缀都是‘sanddog'，而‘sanddog'可以拆分为‘s and dog'和‘sand dog'，会出现重复搜索的过程，这很没有必要，可以利用字典memo来保存，{’sanddog':['sand dog', 's and dog']}，遇到已经出现过的情况，直接查字典即可，速度会快很多


#### 代码实现
```python
class Solution(object):
    def wordBreak(self, s, wordDict):
        """
        :type s: str
        :type wordDict: List[str]
        :rtype: List[str]
        """
        def dfs(s, wordDict, memo):
            if s in memo:
                return memo[s]
            if not s: return []
            res = []
            for word in wordDict:
                if not s.startswith(word):
                    continue
                if len(word) == len(s):
                    res.append(word)
                else:
                    rest = dfs(s[len(word):], wordDict, memo)
                    for item in rest:
                        item = word + ' ' + item
                        res.append(item)
            memo[s] = res
            return res
               
        return dfs(s, wordDict,{})
```
本文链接：[https://www.jianshu.com/p/e36eaa9b91b2](https://www.jianshu.com/p/e36eaa9b91b2)

 
