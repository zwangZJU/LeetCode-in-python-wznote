 [题目链接](https://leetcode-cn.com/problems/continuous-subarray-sum/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、前缀和
***
给定一个包含非负数的数组和一个目标整数 k，编写一个函数来判断该数组是否含有连续的子数组，其大小至少为 2，总和为 k 的倍数，即总和为 n*k，其中 n 也是一个整数。
 
**示例1**
> 输入: [23,2,4,6,7], k = 6
输出: True
解释: [2,4] 是一个大小为 2 的子数组，并且和为 6。

**示例2**
> 输入: [23,2,6,4,7], k = 6
输出: True
解释: [23,2,6,4,7]是大小为 5 的子数组，并且和为 42。

#### 解题思路
***
 用pre_sum保存到第i个元素为止的 前缀和%k，因为倍数对结果的影响不大，而用余数有奇效

例如，nums=[11,2,4], k = 6
i=0: 11%6 = 5,
i=1: (5+2)%6 = 1
i=2: (1+4)%6 = 5
i=0和i=2时的结果相同，刚好2+4是6的倍数，返回True

结论：到每一位时都计算当前的累积和，并对k取模，保存起来，若出现相同的值，则存在符合要求的连续子数组

还要保证至少是两个数字
还要考虑k=0的情况


#### 代码实现
```python
class Solution(object):
    def checkSubarraySum(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: bool
        """
        if k == 0:
            return '00' in ''.join(map(str, nums))
        pre_sum = {0:-1}
        cur_sum = 0
        for i, num in enumerate(nums):
            cur_sum = (num + cur_sum) % k
            if cur_sum in pre_sum and i - pre_sum[cur_sum] > 1:               
                return True
            if cur_sum not in pre_sum:
                pre_sum[cur_sum] = i
        return False
 
```

本文链接：[https://www.jianshu.com/p/69ef7dbca54e](https://www.jianshu.com/p/69ef7dbca54e)
