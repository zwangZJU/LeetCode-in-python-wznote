 [题目链接](https://leetcode-cn.com/problems/subarray-sum-equals-k/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、前缀和
***
 给定一个整数数组和一个整数 k，你需要找到该数组中和为 k 的连续的子数组的个数。

 
**示例**
> 输入:nums = [1,1,1], k = 2
输出: 2 , [1,1] 与 [1,1] 为两种不同的情况。

#### 解题思路
***
前缀和
 P[i] = A[0] + A[1] + ... + A[i-1]
P[j] = A[0] + A[1] + ... + A[j-1]
那么P[j] - P[i] = A[i] + A[i+1] + ... + A[j-1]。
如果P[j] - P[i] == S的话，那么[i,j]就是符合条件的区间。所以对于每个j，只要计算有多少个i使得P[j] - P[i] == S，
 


#### 代码实现
```
class Solution(object):
    def subarraySum(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: int
        """ 
        pre_sum = {0:1}
        cur_sum = 0
        res = 0
        for num in nums:
            cur_sum += num           
            if cur_sum - k in pre_sum:            
                res += pre_sum[cur_sum-k]               
            pre_sum[cur_sum] = pre_sum[cur_sum] + 1 if cur_sum in pre_sum else 1
        return res
```

本文链接：[https://www.jianshu.com/p/a634f3238eb8](https://www.jianshu.com/p/a634f3238eb8)
