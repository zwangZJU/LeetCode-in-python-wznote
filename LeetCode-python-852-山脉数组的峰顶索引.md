 [题目链接](https://leetcode-cn.com/problems/peak-index-in-a-mountain-array/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、二分法
***
 我们把符合下列属性的数组 A 称作山脉：

A.length >= 3
存在 0 < i < A.length - 1 使得A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1]
给定一个确定为山脉的数组，返回任何满足 A[0] < A[1] < ... A[i-1] < A[i] > A[i+1] > ... > A[A.length - 1] 的 i 的值。

 
**示例1**
> 输入：[0,1,0]
输出：1

**示例2**
>输入：[0,2,1,0]
输出：1

#### 解题思路
***
 二分法
同[LeetCode-python 162.寻找峰值](https://www.jianshu.com/p/3e2efbf8e86c)




#### 代码实现
```python
class Solution(object):
    def peakIndexInMountainArray(self, A):
        """
        :type A: List[int]
        :rtype: int
        """
        left = 0
        right = len(A)-1
        while left<right:
            mid = (left+right)//2
            if A[mid]<A[mid+1]:
                left = mid+1
            else:
                right = mid
        return left
```

本文链接：[https://www.jianshu.com/p/3d0c51b61204](https://www.jianshu.com/p/3d0c51b61204)
