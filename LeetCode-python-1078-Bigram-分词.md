 [题目链接](https://leetcode-cn.com/problems/maximal-square/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 给出第一个词 first 和第二个词 second，考虑在某些文本 text 中可能以 "first second third" 形式出现的情况，其中 second 紧随 first 出现，third 紧随 second 出现。

对于每种这样的情况，将第三个词 "third" 添加到答案中，并返回答案。
 
 
**示例1**
> 输入：text = "alice is a good girl she is a good student", first = "a", second = "good"
输出：["girl","student"]

**示例2**
>输入：text = "we will we will rock you", first = "we", second = "will"
输出：["we","rock"]

 
#### 代码实现
```python
class Solution:
    def findOcurrences(self, text: str, first: str, second: str) -> List[str]:
        words = text.split()
        n, res = len(words), []
        for i in range(n-2):
            if words[i]==first and i+1<n and words[i+1]==second and i+2<n:
                res.append(words[i+2])
        return res
```
本文链接：[https://www.jianshu.com/p/fa4c388fa1a3](https://www.jianshu.com/p/fa4c388fa1a3)
