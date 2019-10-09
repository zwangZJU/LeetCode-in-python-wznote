 [题目链接](https://leetcode-cn.com/problems/next-permutation/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 实现获取下一个排列的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。

如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。

必须原地修改，只允许使用额外常数空间。

 
 
**示例**
> 1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1

#### 解题思路
***
 1376542 的下一个排列为 1423567
可以看出，需要改变的子数组的起始数为 从后往前第一个nums[i]>nums[i-1]的数k，即3
要把起始数k替换为从后往前第一个大于k的数，即4，交换两数变为1476532
翻转i之后的一半数组

有一种特殊情况：倒序遍历到0都没有碰到nums[i]>nums[i-1]的情况，直接翻转整个数组



#### 代码实现
```python
class Solution(object):
    def nextPermutation(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        i = j = n-1
        while i > 0 and nums[i-1] >= nums[i]:
            i -= 1  
        k = i - 1    # find the last "ascending" position
        if k>=0:
            while nums[j] <= nums[k]:
                j -= 1
            nums[k], nums[j] = nums[j], nums[k]  
        l, r = k+1, n-1  # reverse the second part
        while l < r:
            nums[l], nums[r] = nums[r], nums[l]
            l +=1 ; r -= 1
```

本文链接：[https://www.jianshu.com/p/735a067d9a1e](https://www.jianshu.com/p/735a067d9a1e)
