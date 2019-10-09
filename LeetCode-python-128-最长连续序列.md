 [题目链接](https://leetcode-cn.com/problems/longest-consecutive-sequence/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  哈希
***
 给定一个未排序的整数数组，找出最长连续序列的长度。

要求算法的时间复杂度为 O(n)。

 
**示例**
> 输入: [100, 4, 200, 1, 3, 2]
输出: 4
解释: 最长连续序列是 [1, 2, 3, 4]。它的长度为 4。

#### 解题思路
***
 1. 先把list用set转换一下，相当于哈希了一下，这样查起来很快
2. 遍历集合中的元素，若该元素为x，且x-1不在集合中，说明它是某一个连续序列的起点，找x+1是否在集合中，如果在，把x+1赋值给x，再找x+1是否在集合中，若一直在，序列的长度就一直增加，如果不在，计算当前的序列长度
3. 若该元素为x，且x-1在集合中，不管它，因为它一定不是某段连续区间的起点


#### 代码实现
```python
class Solution(object):
    def longestConsecutive(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        nums = set(nums)
        longest = 0
        for num in nums:
            if num-1 not in nums:
                end = num + 1
                while end in nums:
                    end += 1
                longest = max(longest, end-num)
        return longest
```
本文链接：[https://www.jianshu.com/p/08adcc2e8aaa](https://www.jianshu.com/p/08adcc2e8aaa)

 
