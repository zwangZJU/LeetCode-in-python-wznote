 [题目链接](https://leetcode-cn.com/problems/jump-game/description/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：贪心算法
***
给定一个非负整数数组，你最初位于数组的第一个位置。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

判断你是否能够到达最后一个位置。

**示例1**
>输入: [2,3,1,1,4]
输出: true
解释: 从位置 0 到 1 跳 1 步, 然后跳 3 步到达最后一个位置。

**示例2**
>输入: [3,2,1,0,4]
输出: false
解释: 无论怎样，你总会到达索引为 3 的位置。但该位置的最大跳跃长度是 0 ， 所以你永远不可能到达最后一个位置。
#### 解题思路
***
设置一个位置指针i，在每一个位置i都寻找当前能到达的最远的位置reach，当i到达数组末尾，则为True，若i>reach，则为False
#### 代码实现
```
class Solution:
    def canJump(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        reach = 0
        i = 0
        n = len(nums)
        while i<n and i<= reach:
            reach = max(i+nums[i], reach)
            i += 1
        return i==n
```

本文链接：[https://www.jianshu.com/p/98a348db371f](https://www.jianshu.com/p/98a348db371f)
