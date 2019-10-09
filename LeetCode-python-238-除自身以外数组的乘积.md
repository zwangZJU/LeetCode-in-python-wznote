 [题目链接](https://leetcode-cn.com/problems/product-of-array-except-self/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定长度为 n 的整数数组 nums，其中 n > 1，返回输出数组 output ，其中 output[i] 等于 nums 中除 nums[i] 之外其余各元素的乘积。

 
**示例**
> 输入: [1,2,3,4]
输出: [24,12,8,6]

说明: 请不要使用除法，且在 O(n) 时间复杂度内完成此题。

进阶：
你可以在常数空间复杂度内完成这个题目吗？（ 出于对空间复杂度分析的目的，输出数组不被视为额外空间。）
#### 解题思路
***
 先求每个数左边的数组的乘积
再求每个数右边的数组的乘积
最后左右两边的乘积相乘就是最后的结果



#### 代码实现
```
class Solution(object):
    def productExceptSelf(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        n = len(nums)
        res = [1]*n
         
        
        for i in range(n-1):            
            res[i+1] = res[i] * nums[i]
        right = 1
        for i in range(n-1,-1,-1):
           
            res[i] *= right
            right *= nums[i]
           
        return res
```

本文链接：[https://www.jianshu.com/p/32ac6def6a6b](https://www.jianshu.com/p/32ac6def6a6b)
