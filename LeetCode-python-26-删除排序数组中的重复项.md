[题目链接](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个排序数组，你需要在**[原地](http://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95)**删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在**[原地](https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95)修改输入数组**并在使用 O(1) 额外空间的条件下完成。


 
**示例1**
> 给定数组 nums = [1,1,2], 
函数应该返回新的长度 2, 并且原数组 nums 的前两个元素被修改为 1, 2。 
你不需要考虑数组中超出新长度后面的元素。

**示例2**
>给定 nums = [0,0,1,1,1,2,2,3,3,4],
函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。
你不需要考虑数组中超出新长度后面的元素。

#### 解题思路
***
 双指针法：
初始时，后指针为0，前指针为1
当 前指针和后指针指向的数字相等，前指针向前一步
当  前指针和后指针指向的数字不同，后指针向前一步，把前指针指向的数字赋给后指针指向的位置



#### 代码实现
```
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if not nums:
            return 0
        i = 0
        for j in range(1, len(nums)):
            if nums[i]!=nums[j]:
                i += 1
                nums[i] = nums[j]
        return i+1
                
```

本文链接：[https://www.jianshu.com/p/098ecda3471f](https://www.jianshu.com/p/098ecda3471f)
