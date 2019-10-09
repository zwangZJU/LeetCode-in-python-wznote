 [题目链接](https://leetcode-cn.com/problems/increasing-triplet-subsequence/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组  
***
 给定一个未排序的数组，判断这个数组中是否存在长度为 3 的递增子序列。

数学表达式如下:

如果存在这样的 i, j, k,  且满足 0 ≤ i < j < k ≤ n-1，
使得 arr[i] < arr[j] < arr[k] ，返回 true ; 否则返回 false 。
说明: 要求算法的时间复杂度为 O(n)，空间复杂度为 O(1) 。
 
 
**示例1**
> 输入: [1,2,3,4,5]
输出: true

**示例2**
>输入: [5,4,3,2,1]
输出: false

#### 解题思路
***
 遍历数组，当前的最小值可以做first，second要比first大，且尽可能的小，后续只要有大于second的值就能返回True，遍历到最后还不True的就返回False



#### 代码实现
```python
class Solution(object):
    def increasingTriplet(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        first = float('inf')
        second = float('inf')
        for num in nums:
            if first>=num:
                first = num
            elif second>num:
                second = num
            elif num>second:
                return True
        return False
```

本文链接：[https://www.jianshu.com/p/70b741669373](https://www.jianshu.com/p/70b741669373)
