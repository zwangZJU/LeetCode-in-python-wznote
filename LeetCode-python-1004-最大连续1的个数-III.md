 [题目链接](https://leetcode-cn.com/problems/max-consecutive-ones-iii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、双指针
***
 给定一个由若干 0 和 1 组成的数组 A，我们最多可以将 K 个值从 0 变成 1 。

返回仅包含 1 的最长（连续）子数组的长度。

 
**示例1**
> 输入：A = [1,1,1,0,0,0,1,1,1,1,0], K = 2
输出：6
解释： 
[1,1,1,0,0,1,1,1,1,1,1]
粗体数字从 0 翻转到 1，最长的子数组长度为 6。

 **示例2**
>输入：A = [0,0,1,1,0,0,1,1,1,0,1,1,0,0,0,1,1,1,1], K = 3
输出：10
解释：
[0,0,1,1,1,1,1,1,1,1,1,1,0,0,0,1,1,1,1]
粗体数字从 0 翻转到 1，最长的子数组长度为 10。

 
#### 解题思路
***
 双指针，维持两个指针之间只有k个0



#### 代码实现
```python
class Solution(object):
    def longestOnes(self, A, K):
        """
        :type A: List[int]
        :type K: int
        :rtype: int
        """
        l, res = 0, 0
        stack = []
        for r in range(len(A)):
            if A[r] == 0:
                stack.append(r)
            if len(stack)>K:
                l = stack.pop(0)+1
            else:
                res = max(res, r-l+1)
                
        return res 
```

本文链接：[https://www.jianshu.com/p/3acc51698d71](https://www.jianshu.com/p/3acc51698d71)
