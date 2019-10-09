 [题目链接](https://leetcode-cn.com/problems/increasing-subsequences/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、深度优先搜索
***
 给定一个整型数组, 你的任务是找到所有该数组的递增子序列，递增子序列的长度至少是2。

 
**示例**
> 输入: [4, 6, 7, 7]
输出: [[4, 6], [4, 7], [4, 6, 7], [4, 6, 7, 7], [6, 7], [6, 7, 7], [7,7], [4,7,7]]

 
#### 解题思路
***
 类似于求所有子序列
只多了两个条件：
1. 在添加一个元素时，只需考虑它是否大于等于当前子序列的最后一个值
2. 子序列长度大于2


注意：
记录用过的数字，避免重复



#### 代码实现
```
class Solution(object):
    def findSubsequences(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        res = []
        self.n = len(nums)
        def dfs(index, path):
            if len(path)>=2:
                res.append(path)
      
            if index>=self.n:
                return
            used = {}
            for i in range(index, self.n):
                if nums[i] in used: continue
                used[nums[i]] = True
                if not path or nums[i]>=path[-1] :
                    dfs(i+1, path+[nums[i]])
        dfs(0, [])
        return res
```

本文链接：[https://www.jianshu.com/p/8fa9e12a5f28](https://www.jianshu.com/p/8fa9e12a5f28)
