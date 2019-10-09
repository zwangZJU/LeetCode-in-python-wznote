 [题目链接](https://leetcode-cn.com/problems/shortest-word-distance/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、字符串
***
 给定一个单词列表和两个单词 word1 和 word2，返回列表中这两个单词之间的最短距离。

示例:
假设 words = ["practice", "makes", "perfect", "coding", "makes"]

**示例1**
> 输入: word1 = “coding”, word2 = “practice”
输出: 3
**示例2**
> 输入: word1 = "makes", word2 = "coding"
输出: 1

注意:
你可以假设 word1 不等于 word2, 并且 word1 和 word2 都在列表里。



#### 代码实现
```python
class Solution(object):
    def shortestDistance(self, words, word1, word2):
        """
        :type words: List[str]
        :type word1: str
        :type word2: str
        :rtype: int
        """
        
        res = len(words)
        pos1, pos2 = None, None
        for idx, word in enumerate(words):
            if word == word1:
                pos1 = idx
            elif word == word2:
                pos2 = idx
            if pos1 is not None and pos2 is not None:
            
                res = min(res, abs(pos1 - pos2))
        return res

```

本文链接：[https://www.jianshu.com/p/1377d73b0904](https://www.jianshu.com/p/1377d73b0904)
