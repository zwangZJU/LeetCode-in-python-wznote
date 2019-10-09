 [题目链接](https://leetcode-cn.com/problems/kth-smallest-element-in-a-sorted-matrix/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、二分查找
***
 给定一个 n x n 矩阵，其中每行和每列元素均按升序排序，找到矩阵中第k小的元素。
请注意，它是排序后的第k小元素，而不是第k个元素。

 
**示例**
> matrix = [
   [ 1,  5,  9],
   [10, 11, 13],
   [12, 13, 15]
],
k = 8,
返回 13。

#### 解题思路
***
 初始时，最小值l为matrix[0][0],最大值h为matrix[n-1][m-1]，
1. 中值mid=(l+h)/2， 计算mid的位置，是第j小的数
2. 当j<k时, l = mid+1; 当j>k时, h=mid
重复上述步骤，直到不符合l<h



#### 代码实现
```
class Solution(object):
    def kthSmallest(self, matrix, k):
        """
        :type matrix: List[List[int]]
        :type k: int
        :rtype: int
        """
        n, m = len(matrix), len(matrix[0])
        l, h = matrix[0][0], matrix[n-1][m-1]
        
        while l < h:
            count = 0
            mid = l + (h-l)//2
            for i in range(n):
                j = m-1
                while j>=0 and matrix[i][j]>mid:
                    j -= 1               
                count += j+1
                #print(count, k)
            if count>=k:
                h = mid
            else:
                l = mid + 1
        return l
```

本文链接：[https://www.jianshu.com/p/04289b55120a](https://www.jianshu.com/p/04289b55120a)
