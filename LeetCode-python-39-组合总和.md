 [题目链接](https://leetcode-cn.com/problems/combination-sum/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：深度优先搜索  
***
 给定一个无重复元素的数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。

candidates 中的数字可以无限制重复被选取。
 
**示例1**
> 输入: candidates = [2,3,6,7], target = 7,
所求解集为:
[
  [7],
  [2,2,3]
]

**示例2**
>输入: candidates = [2,3,5], target = 8,
所求解集为:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]

 
#### 解题思路
***
 典型的深度优先搜索，每次加入一个数nums[i]，target就更新为target-nums[i]
搜索结束的条件:
1. target<0,这条路径的和不为target，放弃
2. target==0, 这条可以，收入囊中



#### 代码实现
```python
class Solution(object):
    def combinationSum(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        length = len(candidates)
         
        res = []
        def dfs( target, index, maybe):
            if target < 0:
                return
            if target == 0:
                res.append(maybe)
                return 
            for i in range(index, length):
                dfs(target-candidates[i], i, maybe+[candidates[i]])
        
        dfs(target, 0, [])
        return res
```

本文链接：[https://www.jianshu.com/p/82e6885f0871](https://www.jianshu.com/p/82e6885f0871)
