 [题目链接](https://leetcode-cn.com/problems/group-anagrams/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。
 
**示例**
> 输入: ["eat", "tea", "tan", "ate", "nat", "bat"],
输出:
[
  ["ate","eat","tea"],
  ["nat","tan"],
  ["bat"]
]

 
#### 解题思路
***
 对每个字符串排序，排完序相等的属于同一组。用字典会快一点


#### 代码实现
```python
class Solution(object):
    def groupAnagrams(self, strs):
        """
        :type strs: List[str]
        :rtype: List[List[str]]
        """
        d = {}
        for s in strs:
            key = tuple(sorted(s))
            d[key] = d.get(key, []) + [s]
        return d.values()
```

本文链接：[https://www.jianshu.com/p/bbd7714da71a](https://www.jianshu.com/p/bbd7714da71a)
