[题目链接](https://leetcode-cn.com/problems/single-number/)
难度： 简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组
***
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。
**示例1**
>输入: [2,2,1]
输出: 1

**示例2**
>输入: [4,1,2,1,2]
输出: 4

#### 解题思路
***
两个相同的数经过异或操作之后是0，0和任何数异或的结果为其本身，且异或服从交换律，所以对所有数字进行异或的结果就是只出现一次的数字
#### 代码实现
```
class Solution(object):
    def singleNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        res = nums[0]
        for i in range(1,len(nums)):
            res ^= nums[i]
        return res
```

本文链接：[https://www.jianshu.com/p/f3c2a20da915](https://www.jianshu.com/p/f3c2a20da915)
