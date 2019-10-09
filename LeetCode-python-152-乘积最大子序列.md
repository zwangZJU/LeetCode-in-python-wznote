 [题目链接](https://leetcode-cn.com/problems/maximum-product-subarray/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划
***
给定一个整数数组 nums ，找出一个序列中乘积最大的连续子序列（该序列至少包含一个数）。
**示例1**
>输入: [2,3,-2,4]
输出: 6
解释: 子数组 [2,3] 有最大乘积 6。

**示例2**
>输入: [-2,0,-1]
输出: 0
解释: 结果不能为 2, 因为 [-2,-1] 不是子数组。

#### 解题思路
***
乘积子数组中可能有正数、负数，也可能有 0。因为有负数的存在，所以可以考虑同时找出最大乘积和最小乘积。于是，问题简化成这样：在数组中找到一个子数组，使得它的乘积最大，同时再找到另一个子数组，使得它的乘积最小（含有负数的情况）。也就是说，不但记录最大乘积，也记录最小乘积。

  假设数组为 a[]，直接利用动态规划来求解。考虑到负数的情况，用maxend来表示以 a[i]结尾的最大连续子数组的乘积值，用 minend 表示以 a[i]结尾的最小连续子数组的乘积值，那么状态转移方程为：
maxend = max(max(maxend * a[i], minend * a[i]), a[i]);
minend = min(min(maxend * a[i], minend * a[i]), a[i]); 
#### 代码实现
```
class Solution(object):
    def maxProduct(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        dp_max = [nums[0]]*n
        dp_min = [nums[0]]*n
        res = nums[0]
        for i in range(1,n):  
            dp_max[i] = max(dp_max[i-1]*nums[i], nums[i], dp_min[i-1]*nums[i])
            dp_min[i] = min(dp_max[i-1]*nums[i], nums[i], dp_min[i-1]*nums[i])
            res = max(res,dp_max[i])           
        return res
```

本文链接：[https://www.jianshu.com/p/95aea622f481](https://www.jianshu.com/p/95aea622f481)
