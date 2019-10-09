 [题目链接](https://leetcode-cn.com/problems/find-common-characters/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给定仅有小写字母组成的字符串数组 A，返回列表中的每个字符串中都显示的全部字符（包括重复字符）组成的列表。例如，如果一个字符在每个字符串中出现 3 次，但不是 4 次，则需要在最终答案中包含该字符 3 次。

你可以按任意顺序返回答案。
 
 
**示例1**
> 输入：["bella","label","roller"]
输出：["e","l","l"]

**示例2**
>输入：["cool","lock","cook"]
输出：["c","o"]

#### 解题思路
***
 统计字符串中字符的个数，选在每个字符中最小的值



#### 代码实现
```python
from collections import Counter
class Solution:
    def commonChars(self, A: List[str]) -> List[str]:
        common_counter = Counter(A[0])
        for a in A[1:]:
            common_counter &= Counter(a)
         
        return list(common_counter.elements())
```

本文链接：[https://www.jianshu.com/p/44fbf3d302fb](https://www.jianshu.com/p/44fbf3d302fb)
