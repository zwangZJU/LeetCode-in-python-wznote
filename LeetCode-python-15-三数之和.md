 [题目链接](https://leetcode-cn.com/problems/3sum/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。

注意：答案中不可以包含重复的三元组。

 
**示例**
> 给定数组 nums = [-1, 0, 1, 2, -1, -4]，
满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]

#### 解题思路
***
 双指针法：
数组先从小到大排序
从第0个数到第n-2个数进行遍历，当到第i个数时，左指针left指向i+1,右指针指向n-1，这三个数之和位sum：
若sum>0,right-1;
若sum<0,left+1;
若sum=0,保存这三个数

为了不重复，当第i个数等于第i-1个数时，跳过



#### 代码实现
```
class Solution(object):
    def threeSum(self, nums):
        """
        :type nums: List[int]
        :rtype: List[List[int]]
        """
        nums = sorted(nums)
        res = []
        for i in range(len(nums)-2):
            left = i+1
            right = len(nums)-1
            if i>0 and nums[i] == nums[i-1]:
                continue
             
            while left<right:
                c = nums[i]+nums[left]+nums[right]
                if c == 0:

                    res.append([nums[i], nums[left], nums[right]])
                    
                    while nums[right] == nums[right-1] and right>left:
                        right -= 1
                                           
                    while nums[left] == nums[left+1] and right>left:
                        left += 1
                    left +=1
                    right -= 1
                elif c>0:
                    
                    right -= 1
                else:
                   
                    left += 1
                
        return res
```

本文链接：[https://www.jianshu.com/p/fdfe1ce735ff](https://www.jianshu.com/p/fdfe1ce735ff)
