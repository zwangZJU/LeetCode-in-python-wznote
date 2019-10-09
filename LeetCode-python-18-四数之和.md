 [题目链接](https://leetcode-cn.com/problems/4sum/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个包含 n 个整数的数组 nums 和一个目标值 target，判断 nums 中是否存在四个元素 a，b，c 和 d ，使得 a + b + c + d 的值与 target 相等？找出所有满足条件且不重复的四元组。

注意：
答案中不可以包含重复的四元组。

 
**示例**
> 给定数组 nums = [1, 0, -1, 0, -2, 2]，和 target = 0。
满足要求的四元组集合为：
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]

 
#### 解题思路
***
1.排序
 2.在[三数之和](https://www.jianshu.com/p/fdfe1ce735ff)
的外面加一层循环
遇到相同的数要跳过，以免重复


#### 代码实现
```python
class Solution(object):
    def fourSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[List[int]]
        """
        nums = sorted(nums)
        res = []
        len_nums = len(nums)
        for i in range(len_nums-3):
            if i-1>=0 and nums[i]==nums[i-1]:
                continue
            for j in range(i+1, len_nums-2):
                if j-1>i and nums[j] == nums[j-1]:
                    continue
                start = j+1
                end = len_nums-1
                while start<end:
                    sum = nums[i] + nums[j] + nums[start] + nums[end]
                    if sum == target:
                        res.append([nums[i],nums[j], nums[start], nums[end]])
                        while start<end and nums[start]==nums[start+1]:
                            start += 1
                        while start<end and nums[end] == nums[end-1]:
                            end -= 1
                        start += 1
                        end -= 1
                    elif sum > target:
                        end -= 1
                    else:
                        start += 1
                    
        return res
```

本文链接：[https://www.jianshu.com/p/d13071cd072a](https://www.jianshu.com/p/d13071cd072a)
