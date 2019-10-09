 [题目链接](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array-ii/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组
***
给定一个排序数组，你需要在**[原地](http://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95)**删除重复出现的元素，使得每个元素最多出现两次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在**[原地](https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95)修改输入数组**并在使用 O(1) 额外空间的条件下完成。

**示例1**
>给定 nums = [1,1,1,2,2,3],
函数应返回新长度 length = 5, 并且原数组的前五个元素被修改为 1, 1, 2, 2, 3 。
你不需要考虑数组中超出新长度后面的元素。

**示例2**
>给定 nums = [0,0,1,1,1,1,2,3,3],
函数应返回新长度 length = 7, 并且原数组的前五个元素被修改为 0, 0, 1, 1, 2, 3, 3 。
你不需要考虑数组中超出新长度后面的元素。

#### 解题思路
***
因为是排序数组，后面的数肯定大于前面的数
只要保证第i+2个数大于第i个数就行

#### 代码实现
```
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:     
        index = 0
        for num in nums:
            if index<2 or num>nums[index-2]:
                nums[index] = num
                index += 1
        return index
```

本文链接：[https://www.jianshu.com/p/6f5812c05889](https://www.jianshu.com/p/6f5812c05889)
