 [题目链接](https://leetcode-cn.com/problems/subsets/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、动态规划
***
 给定一组不含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。

说明：解集不能包含重复的子集。

 
**示例**
> 输入: nums = [1,2,3]
输出:
[
  [3],
  [1],
  [2],
  [1,2,3],
  [1,3],
  [2,3],
  [1,2],
  []
]

#### 解题思路
***
1到n的数列的子集 = 1到n-1的数列的全部子集 + 1到n-1的数列的每一个子集都加上n



#### 代码实现
```
class Solution(object):
    def subsets(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        dp = [[]]
        for num in nums:
            dp = dp + [item+[num] for item in dp]
        return dp
```

本文链接：[https://www.jianshu.com/p/feff63c9e933](https://www.jianshu.com/p/feff63c9e933)
