 [题目链接](https://leetcode-cn.com/problems/3sum-closest/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 
给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。
 
**示例**
> 例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.
与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).

#### 解题思路
***
  双指针法：
数组先从小到大排序
cur_closest用来保存当前最接近的和
从第0个数到第n-2个数进行遍历，当到第i个数时，左指针left指向i+1,右指针指向n-1，这三个数之和位sum：
若sum-target>0,right-1;
若sum-target<0,left+1;
当abs(sum-target)<abs(cur_closest-target)时，修改cur_closest为sum
若sum-target=0,保存这三个数




#### 代码实现
```
class Solution(object):
    def threeSumClosest(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        nums.sort()
   
        res = nums[0] + nums[1] + nums[2]
        
        for i in range(len(nums)-2):
            l, r = i+1, len(nums)-1
            while l<r:
                sum = nums[i] + nums[l] + nums[r]
                if sum == target:
                    return sum
                if abs(res-target)>abs(sum-target):
                    res = sum
                if sum<target:
                    l += 1
                else:
                    r -= 1
        return res
```

本文链接：[https://www.jianshu.com/p/29041b25916c](https://www.jianshu.com/p/29041b25916c)
