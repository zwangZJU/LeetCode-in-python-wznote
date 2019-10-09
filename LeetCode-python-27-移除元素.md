 [题目链接](https://leetcode-cn.com/problems/remove-element/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 数组
***
 给定一个数组 nums 和一个值 val，你需要原地移除所有数值等于 val 的元素，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

元素的顺序可以改变。你不需要考虑数组中超出新长度后面的元素。
 
**示例1**
> 给定 nums = [3,2,2,3], val = 3,
函数应该返回新的长度 2, 并且 nums 中的前两个元素均为 2。
你不需要考虑数组中超出新长度后面的元素。

**示例2**
> 给定 nums = [0,1,2,2,3,0,4,2], val = 2,
函数应该返回新的长度 5, 并且 nums 中的前五个元素为 0, 1, 3, 0, 4。
注意这五个元素可为任意顺序。
你不需要考虑数组中超出新长度后面的元素。

#### 解题思路
***
 双指针
j用来遍历数组，i用来记录删掉val后的长度
只有nums[j]不等于val时，i才加1，并且将nums[j]赋给nums[i],这样就保证了是原地修改

#### 代码实现
```python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """        
        i, n = 0, len(nums)
        for j in range(0, n):            
            if nums[j] != val:
                nums[i] = nums[j]
                i += 1                
        return i
```

本文链接：[https://www.jianshu.com/p/94b23b608d82](https://www.jianshu.com/p/94b23b608d82)
