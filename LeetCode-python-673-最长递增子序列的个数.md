 [题目链接](https://leetcode-cn.com/problems/number-of-longest-increasing-subsequence/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
 给定一个未排序的整数数组，找到最长递增子序列的个数。

 
**示例1**
> 输入: [1,3,5,4,7]
输出: 2
解释: 有两个最长递增子序列，分别是 [1, 3, 4, 7] 和[1, 3, 5, 7]。

**示例2**
>输入: [2,2,2,2,2]
输出: 5
解释: 最长递增子序列的长度是1，并且存在5个子序列的长度为1，因此输出5。

#### 解题思路
***
 要求个数，首先还是得求最长的长度
dp_len[i]表示以nums[i]结尾的最长递增子序列的长度
dp_count[i]表示以nums[i]结尾的最长递增子序列的个数

求最长长度的方法：
遍历nums[i]之前的所有数，找到所有nums[j]<nums[i]，最长的dp_len[j]+1就是dp_len[i]

求最长长度时的个数的方法：
遍历所有dp_len[j]，其中0<=j<i，依然只关注nums[i]>nums[j]的情况
如果dp_len[j]>= dp_len[i] ，那么dp_count[i] = dp_count[j] 。
如果dp_len[j]== dp_len[i] - 1，那么dp_count[i]+=dp_count[j]


#### 代码实现
```python
class Solution(object):
    def findNumberOfLIS(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        n = len(nums)
        dp_len = [1] * n
        dp_count = [1] * n
        for i in range(1, n):
            for j in range(i):
                if nums[i]>nums[j]:
                    if dp_len[i] <= dp_len[j]:
                        dp_len[i] = dp_len[j] + 1
                        dp_count[i] = dp_count[j]
                    elif dp_len[i] == dp_len[j] + 1:
                        dp_count[i] += dp_count[j]
        longest = max(dp_len)
        return sum(dp_count[i] for i in range(n) if dp_len[i]==longest )
```

本文链接：[https://www.jianshu.com/p/ab8326784a5f](https://www.jianshu.com/p/ab8326784a5f)
