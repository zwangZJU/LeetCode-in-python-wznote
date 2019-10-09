[题目链接](https://leetcode-cn.com/problems/rotate-array/submissions/)

难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。

 
**示例1**
> 输入: [1,2,3,4,5,6,7] 和 k = 3
输出: [5,6,7,1,2,3,4]
解释:
向右旋转 1 步: [7,1,2,3,4,5,6]
向右旋转 2 步: [6,7,1,2,3,4,5]
向右旋转 3 步: [5,6,7,1,2,3,4]

**示例2**
> 输入: [-1,-100,3,99] 和 k = 2
输出: [3,99,-1,-100]
解释: 
向右旋转 1 步: [99,-1,-100,3]
向右旋转 2 步: [3,99,-1,-100]

#### 解题思路
***
先将n-k到第k位的子数组翻转
再将0到第n-k位的子数组翻转
最后将整个数组翻转 

注意：
当k大于数组长度n时，移动k次等于移动k%n次



#### 代码实现
```
class Solution:
    def rotate(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: void Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        k = k%n
        def reverse(nums, i, j):
            left, right = i, j-1
            while left<right:
                nums[left], nums[right] = nums[right], nums[left]
                left += 1
                right -= 1        
        reverse(nums, 0, n-k)       
        reverse(nums, n-k, n)        
        reverse(nums, 0, n)
 
```

本文链接：[https://www.jianshu.com/p/9ac6f21eb671](https://www.jianshu.com/p/9ac6f21eb671)
