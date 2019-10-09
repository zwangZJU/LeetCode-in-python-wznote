[题目链接](https://leetcode-cn.com/problems/jump-game-ii/)

难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个非负整数数组，你最初位于数组的第一个位置。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

你的目标是使用最少的跳跃次数到达数组的最后一个位置。

 
**示例1**
> 输入: [2,3,1,1,4]
输出: 2
解释: 跳到最后一个位置的最小跳跃数是 2。
     从下标为 0 跳到下标为 1 的位置，跳 1 步，然后跳 3 步到达数组的最后一个位置。

#### 解题思路
***
在不得不跳的时候再跳

 cur_max表示跳i步能达到最远的坐标
next_max表示在cur_max之前的位置跳一步能达到下一个最远的位置
例如：
[4,2,7,3,1,1,3,1,1,1]
第一步从4开始，最远跳到数字1的位置，cur_max = 0+4=4
那跳两步最远的位置为max(1+2, 2+7, 3+3, 4+1)中的一个，其中的加法操作是i+nums[i]。不难得出next_max=2+7=9
遍历数组，当i==cur_max，step+1，因为上一次跳跃最远能到cur_max，要超过cur_max必须再跳一次，而再跳一次能达到的最远距离为next_max



#### 代码实现
```
class Solution(object):
    def jump(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        if not n or n == 1:
            return 0
        
        next_max = cur_max = 0
        
        step = 0
        for i in range(n):
            next_max = max(nums[i]+i, next_max)
            if next_max>=n-1:
                return step+1
            if i == cur_max:
                step += 1
                cur_max = next_max
```

本文链接：[https://www.jianshu.com/p/f650c5d22150](https://www.jianshu.com/p/f650c5d22150)
