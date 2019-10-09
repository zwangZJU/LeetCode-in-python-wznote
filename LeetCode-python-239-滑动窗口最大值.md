 [题目链接](https://leetcode-cn.com/problems/sliding-window-maximum/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个数组 nums，有一个大小为 k 的滑动窗口从数组的最左侧移动到数组的最右侧。你只可以看到在滑动窗口 k 内的数字。滑动窗口每次只向右移动一位。

返回滑动窗口最大值。
 

 
**示例**
> 输入: nums = [1,3,-1,-3,5,3,6,7], 和 k = 3
输出: [3,3,5,5,6,7] 
解释: 
  滑动窗口的位置                最大值
[1  3  -1] -3  5  3  6  7        3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7


#### 解题思路
***
 用一个数组index记录滑动窗口中可能是最大值的下标
第一个窗口的index中只保留3和-1的下标，因为有3在，1不可能是最大值
第三个窗口的index中只保留5的下标，因为有5在，-1和-3在滑动过程中也不可能是最大值

所以，当第i个数的下标准备进index时，需要移除所有index中已有下标指向的比第i个数要小的数的下标，如在第三个窗口中，-1，-3的下标都要出index，3的下标也要出index,因为超过了窗口范围
当第i个数小于index最后一个数时，i进index，因为当i前面的下标出index后，i指向的数有可能是最大的



#### 代码实现
```
class Solution(object):
    def maxSlidingWindow(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """
        n = len(nums)
        if n<2 or k==1:
            return nums
        res = []
        index = [0]    
        queue = [nums[0]]
        
        for i in range(1,n):
            
            if index[0]<=i-k:
                index.pop(0)
            while index and nums[index[-1]]<nums[i]:
                index.pop()
            index.append(i)
            if i>=k-1:
                res.append(nums[index[0]])
          
        return res
```

本文链接：[https://www.jianshu.com/p/d765bbf4fc72](https://www.jianshu.com/p/d765bbf4fc72)
