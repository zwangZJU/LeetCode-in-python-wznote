[题目链接](https://leetcode-cn.com/problems/contains-duplicate/)

难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个整数数组，判断是否存在重复元素。

如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。

 
**示例1**
> 输入: [1,2,3,1]
输出: true

**示例2**
>输入: [1,2,3,4]
输出: false

#### 解题思路
***
 比较求集合之后的长度是否等于原数组的长度



#### 代码实现
```
class Solution:
    def containsDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        return not (len(nums) == len(set(nums)))
```

本文链接：[https://www.jianshu.com/p/b5a10b382998](https://www.jianshu.com/p/b5a10b382998)
