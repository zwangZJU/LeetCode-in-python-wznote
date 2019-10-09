 [题目链接](https://leetcode-cn.com/problems/combination-sum-ii/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  深度优先搜索
***
 给定一个数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。

candidates 中的每个数字在每个组合中只能使用一次。
 
**示例1**
> 所求解集为:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]

**示例2**
> 输入: candidates = [2,5,2,1,2], target = 5,
所求解集为:
[
  [1,2,2],
  [5]
]

 
#### 解题思路
***
 “解集不能包含重复的组合”，那就排个序，相邻两数相同， 到第二个就跳过，做到结果的同一位上同样大小的数只使用一个，
剩下的和[39.组合总和](https://www.jianshu.com/p/82e6885f0871)一致



#### 代码实现
```python
class Solution(object):
    def combinationSum2(self, candidates, target):
        """
        :type candidates: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        c = sorted(candidates)
        res = []
        len_c = len(c)
      
        def dfs(target, index, path):
        
        
            if target == 0:
                res.append(path)
                return
           
            for i in range(index, len_c):
                
                if i>index and c[i] == c[i-1]:
                    continue
                if c[i]>target:
                    break
                dfs(target-c[i], i+1, path+[c[i]])
        dfs(target, 0, [])
        return res
```

本文链接：[https://www.jianshu.com/p/56310df4a80a](https://www.jianshu.com/p/56310df4a80a)
