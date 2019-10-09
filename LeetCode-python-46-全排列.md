 [题目链接](https://leetcode-cn.com/problems/permutations/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、深度优先搜索
***
 
给定一个没有重复数字的序列，返回其所有可能的全排列。
 
**示例**
> 输入: [1,2,3]
输出:
[
  [1,2,3],
  [1,3,2],
  [2,1,3],
  [2,3,1],
  [3,1,2],
  [3,2,1]
]

 
#### 解题思路
***
让数组中所有的数都做一次排列的第一个元素，让剩下的数组中的每一个数都做一次第二个数。。。
 



#### 代码实现
```
class Solution(object):
    def permute(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        def dfs(num, path):
            if not num:
                res.append(path)
                return
            for i in range(len(num)):
                dfs(num[:i]+num[i+1:], path+[num[i]])
        dfs(nums, [])
        return res 
```

本文链接：[https://www.jianshu.com/p/e41ef9d22b5a](https://www.jianshu.com/p/e41ef9d22b5a)
