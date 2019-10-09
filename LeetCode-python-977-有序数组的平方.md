 [题目链接](https://leetcode-cn.com/problems/squares-of-a-sorted-array/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个按非递减顺序排序的整数数组 A，返回每个数字的平方组成的新数组，要求也按非递减顺序排序。

 
**示例1**
> 输入：[-4,-1,0,3,10]
输出：[0,1,9,16,100]
 
**示例2**
>输入：[-7,-3,2,3,11]
输出：[4,9,9,49,121]


#### 代码实现
方法1：
```python
class Solution(object):
    def sortedSquares(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        return sorted([x*x for x in A])
```

方法2：
```python
class Solution(object):
    def sortedSquares(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        n = len(A)
        mid = 0
        while mid<n and A[mid]<0 :
            mid += 1 
        left, right = mid-1, mid       
        res = []
        while left>=0 or right<len(A):
            l = A[left] if left>=0 else -abs(A[n-1])-1
            r = A[right] if right<len(A) else abs(A[0])+1
             
            if l + r < 0:
                res.append(r**2)
                right += 1
            else:
                res.append(l**2)
                left -= 1
        return res
```

本文链接：[https://www.jianshu.com/p/291ccc997d59](https://www.jianshu.com/p/291ccc997d59)
