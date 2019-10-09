 [题目链接](https://leetcode-cn.com/problems/predict-the-winner/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
 给定一个表示分数的非负整数数组。 玩家1从数组任意一端拿取一个分数，随后玩家2继续从剩余数组任意一端拿取分数，然后玩家1拿，……。每次一个玩家只能拿取一个分数，分数被拿取之后不再可取。直到没有剩余分数可取时游戏结束。最终获得分数总和最多的玩家获胜。

给定一个表示分数的数组，预测玩家1是否会成为赢家。你可以假设每个玩家的玩法都会使他的分数最大化。

 
**示例1**
> 输入: [1, 5, 2]
输出: False
解释: 一开始，玩家1可以从1和2中进行选择。
如果他选择2（或者1），那么玩家2可以从1（或者2）和5中进行选择。如果玩家2选择了5，那么玩家1则只剩下1（或者2）可选。
所以，玩家1的最终分数为 1 + 2 = 3，而玩家2为 5。
因此，玩家1永远不会成为赢家，返回 False。
 
**示例2**
>输入: [1, 5, 233, 7]
输出: True
解释: 玩家1一开始选择1。然后玩家2必须从5和7中进行选择。无论玩家2选择了哪个，玩家1都可以选择233。
最终，玩家1（234分）比玩家2（12分）获得更多的分数，所以返回 True，表示玩家1可以成为赢家。

 
#### 解题思路
***
 dp[i][j]表示玩家从第i到第j个数选择时，先手比后手多得的分数
先手只有两种选择方式：
1. 选择nums[i]，先手者的得分为nums[i]-dp[i+1][j]，解释下：若a先手，b后手，dp[i+1][j]表示a先手时比b多得得分，当a选择nums[i]时，相当于用了一次选择机会，在i+1到j中选择后处于后手，而b处于先手，则b比a多得dp[i+1][j]分，相当于a比b多得-dp[i+1][j]分
2. 选择nums[j]，先手者得得分为nums[j]-dp[i][j-1]
故动态转移方程为：
dp = max(nums[i]-dp[i+1][j],nums[j]-dp[i][j-1])



#### 代码实现
```python
 class Solution(object):
    def PredictTheWinner(self, nums):
        """
        :type nums: List[int]
        :rtype: bool
        """
        n = len(nums)
        dp = [[0]*n for _ in nums]         
        for j in range(n):
            for i in range(j-1, -1, -1):                 
                dp[i][j] = max(nums[i]-dp[i+1][j], nums[j]-dp[i][j-1])         
        return dp[0][n-1]>=0
```

本文链接：[https://www.jianshu.com/p/dfd04cfc0275](https://www.jianshu.com/p/dfd04cfc0275)
