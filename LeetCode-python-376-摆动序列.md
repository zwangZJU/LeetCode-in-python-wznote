[题目链接](https://leetcode-cn.com/problems/wiggle-subsequence/description/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划
***
如果连续数字之间的差严格地在正数和负数之间交替，则数字序列称为摆动序列。第一个差（如果存在的话）可能是正数或负数。少于两个元素的序列也是摆动序列。

例如， [1,7,4,9,2,5] 是一个摆动序列，因为差值 (6,-3,5,-7,3) 是正负交替出现的。相反, [1,4,7,2,5] 和 [1,7,4,5,5] 不是摆动序列，第一个序列是因为它的前两个差值都是正数，第二个序列是因为它的最后一个差值为零。

给定一个整数序列，返回作为摆动序列的最长子序列的长度。 通过从原始序列中删除一些（也可以不删除）元素来获得子序列，剩下的元素保持其原始顺序。

**示例**
>输入: [1,17,5,10,13,15,10,5,16,8]
输出: 7
解释: 这个序列包含几个长度为 7 摆动序列，其中一个可为[1,17,10,13,10,16,8]。
#### 解题思路
- dp[i]到第i个数时的最长摆动序列
- 遍历整个数组，计算相邻两数之差，记作d = nums[i] - nums[i-1]
- 记录第一处d != 0时的值为sign
- 状态转移方程：
  当d = 0 或 sign*d >= 0 时：dp[i] = dp[i-1]，其中d为当前相邻位置两数的差，sign为上一相邻位置两数的差
  当sign \* d < 0时：dp[i] = dp[i-1] + 1，并修改sign = -sign
#### 代码实现
```
class Solution:
    def wiggleMaxLength(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        n = len(nums)
        if n<2:
            return n
        dp = [0]*n
        dp[0] = 1
        first = True      
        for i in range(1,n):
            d = nums[i] - nums[i-1]
            if d == 0:
                dp[i] = dp[i-1]
            elif first:
                sign = d
                first = False
                dp[i] = dp[i-1]+1
            elif sign*d<0:
                sign = -sign
                dp[i] = dp[i-1]+1
            else:
                dp[i] = dp[i-1]
        return dp[n-1]
```

本文链接：[https://www.jianshu.com/p/cad9d67c0002](https://www.jianshu.com/p/cad9d67c0002)
