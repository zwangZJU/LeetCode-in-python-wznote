 [题目链接](https://leetcode-cn.com/problems/subsets-ii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、深度优先搜索
***
 给定一个可能包含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。

说明：解集不能包含重复的子集。

 
**示例**
> 输入: [1,2,2]
输出:
[
  [2],
  [1],
  [1,2,2],
  [2,2],
  [1,2],
  []
]

#### 解题思路
***
先排序，不然对顺序不敏感就会造成重复
 深度优先搜索，没有终止条件，同一个位置上，出现过的数字就直接跳过



#### 代码实现
```python
class Solution(object):
    def subsetsWithDup(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        nums.sort()
        n = len(nums)
        res = []
        def dfs(index, path):
            res.append(path)
            used = set()
            for i in range(index, n):
                if nums[i] in used:
                    continue
                used.add(nums[i])
                dfs(i+1, path+[nums[i]])
        dfs(0, [])
        return res
```

本文链接：[https://www.jianshu.com/p/06ec87b71031](https://www.jianshu.com/p/06ec87b71031)
