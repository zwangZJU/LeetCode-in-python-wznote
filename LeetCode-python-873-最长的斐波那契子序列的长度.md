 [题目链接](https://leetcode-cn.com/problems/length-of-longest-fibonacci-subsequence/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 如果序列 X_1, X_2, ..., X_n 满足下列条件，就说它是 斐波那契式 的：

n >= 3
对于所有 i + 2 <= n，都有 X_i + X_{i+1} = X_{i+2}
给定一个严格递增的正整数数组形成序列，找到 A 中最长的斐波那契式的子序列的长度。如果一个不存在，返回  0 。

（回想一下，子序列是从原序列 A 中派生出来的，它从 A 中删掉任意数量的元素（也可以不删），而不改变其余元素的顺序。例如， [3, 5, 8] 是 [3, 4, 5, 6, 7, 8] 的一个子序列）

 
**示例1**
> 输入: [1,2,3,4,5,6,7,8]
输出: 5
解释:
最长的斐波那契式子序列为：[1,2,3,5,8] 。

**示例2**
>输入: [1,3,7,11,12,14,18]
输出: 3
解释:
最长的斐波那契式子序列有：
[1,11,12]，[3,11,14] 以及 [7,11,18] 。

 
#### 解题思路
***
 以每个数作为斐波那契序列的第一个数a，以它之后的每一个数都做第二个数b，寻找a+b是否在原数列中
若在，计数器加1，并令a= b, b=a+b，继续判断a+b是否在原数列中
若不在，结算当前的长度，与当前的最大长度比较，更新当前最大长度



#### 代码实现
```python
 class Solution(object):
    def lenLongestFibSubseq(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        s = set(A)
        n = len(A)
        res = 0
        
        for i in range(n-2):
            for j in range(i+1, n-1):
                count = 2
                a, b = A[i], A[j]
                while a+b in s:
                    a, b = b, a+b
                    count += 1
                res = max(res, count)
                
        return res if res>2 else 0
```

本文链接：[https://www.jianshu.com/p/184c6fdd4be2](https://www.jianshu.com/p/184c6fdd4be2)
