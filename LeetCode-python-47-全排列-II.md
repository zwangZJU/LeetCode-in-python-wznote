 [题目链接](https://leetcode-cn.com/problems/permutations-ii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、深度优先搜索
***
 给定一个可包含重复数字的序列，返回所有不重复的全排列。

 
**示例**
> 输入: [1,1,2]
输出:
[
  [1,1,2],
  [1,2,1],
  [2,1,1]
]
#### 解题思路
***
 对于一个数组，先排序，这是为了有相同的数字的时候可以跳过
全排列的思路就是在当前数组中任选一个数作为第一个数，剩下的数字组成一个新的数组，再在该数组中选一个数作为第一个数，依次循环
遇到两个或多个相同的数字，直接跳过，不然会有重复



#### 代码实现
```
class Solution(object):
    def permuteUnique(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        nums.sort()
        res = []
        def dfs(nums, path):
            if not nums:
               
                res.append(path)
                return 
            for i in range(len(nums)):
                if i>0 and nums[i]==nums[i-1]:
                    continue
                dfs(nums[:i]+nums[i+1:], path+[nums[i]])
        dfs (nums, [])
        return res
```

本文链接：[https://www.jianshu.com/p/06b1f25f6f12](https://www.jianshu.com/p/06b1f25f6f12)
