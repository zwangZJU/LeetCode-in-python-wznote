[题目链接](https://leetcode-cn.com/problems/beautiful-array/description/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：分治
***
对于某些固定的 N，如果数组 A 是整数 1, 2, ..., N 组成的排列，使得：

对于每个 i < j，都不存在 k 满足 i < k < j 使得 A[k] * 2 = A[i] + A[j]。

那么数组 A 是漂亮数组。

**示例1**
>输入：4
输出：[2,1,4,3]

**示例2**
>输入：5
输出：[3,1,2,5,4]

#### 解题思路
***
这个问题有一个非常美妙的数学解法。首先我们要证明漂亮数组满足这样几种性质

减法（减去一个数仍然是漂亮数组）

(A[k]−x)∗2=A[k]∗2−2∗x 不等于 (A[i]−x+A[j]−x)

乘法（乘上一个数仍然是漂亮数组）

A[k]∗2∗x  不等于 (A[i]+A[j])∗x=A[i]∗x+A[j]∗x

有了上面这两个性质，我们就可以很快解决这个问题了。我们知道一个数组A可以分为奇数部分A1和偶数部分A2。此时我们如果有一个漂亮数组B，我们根据前面的性质知道2*B-1是一个漂亮数组并且是奇数数组，而2*B也是一个漂亮数组并且是偶数数组。那么我们通过2*B+2*B-1必然可以构成任意一个漂亮数组了。
#### 代码实现
```python
class Solution:
    def beautifulArray(self, N):
        """
        :type N: int
        :rtype: List[int]
        """
        result = [1]
        while len(result)<N:
            result = [2*i-1 for i in result] + [2*j for j in result]
        return [i for i in result if i<=N]
```

本文链接：[https://www.jianshu.com/p/2f0e19682b39](https://www.jianshu.com/p/2f0e19682b39)
