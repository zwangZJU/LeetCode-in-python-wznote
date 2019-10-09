 [题目链接](https://leetcode-cn.com/problems/maximal-square/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 数组、字符串、排序 
***
 给定一组非负整数，重新排列它们的顺序使之组成一个最大的整数。

 
**示例1**
> 输入: [10,2]
输出: 210

**示例2**
>输入: [3,30,34,5,9]
输出: 9534330
#### 解题思路
***
 排序的规则：
两个字符串数字a,b
若a+b<b+a,则a<b



#### 代码实现
```
class Solution(object):
    def largestNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: str
        """
        nums = [str(x) for x in nums]
        nums = sorted(nums, cmp= lambda x, y : cmp(x+y, y+x), reverse=True)
        return ''.join(nums).lstrip('0') or '0'
```

本文链接：[https://www.jianshu.com/p/2f94677d8117](https://www.jianshu.com/p/2f94677d8117)
