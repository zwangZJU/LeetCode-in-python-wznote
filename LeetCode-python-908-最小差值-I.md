 [题目链接](https://leetcode-cn.com/problems/smallest-range-i/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、数学
***
给定一个整数数组 A，对于每个整数 A[i]，我们可以选择任意 x 满足 -K <= x <= K，并将 x 加到 A[i] 中。

在此过程之后，我们得到一些数组 B。

返回 B 的最大值和 B 的最小值之间可能存在的最小差值。

 
**示例1**
> 输入：A = [1], K = 0
输出：0
解释：B = [1]

**示例2**
>输入：A = [0,10], K = 2
输出：6
解释：B = [2,8]

**示例3**
>输入：A = [1,3,6], K = 3
输出：0
解释：B = [3,3,3] 或 B = [4,4,4]

#### 解题思路
***
 数组最大值为max，最小值为min
若max-K<min+K, 最小差为0
否则，最小差为(max-K) - (min+l)



#### 代码实现
```python
class Solution(object):
    def smallestRangeI(self, A, K):
        """
        :type A: List[int]
        :type K: int
        :rtype: int
        """         
        return max(0, max(A)-K - min(A)-K) 
```

本文链接：[https://www.jianshu.com/p/815ef879cdb5](https://www.jianshu.com/p/815ef879cdb5)
