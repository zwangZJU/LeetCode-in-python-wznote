 [题目链接](https://leetcode-cn.com/problems/sort-array-by-parity/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  双指针
***
 给定一个非负整数数组 A，返回一个数组，在该数组中， A 的所有偶数元素之后跟着所有奇数元素。

你可以返回满足此条件的任何数组作为答案。

 
**示例**
> 输入：[3,1,2,4]
输出：[2,4,3,1]
输出 [4,2,3,1]，[2,4,1,3] 和 [4,2,1,3] 也会被接受。
#### 解题思路
***
 双指针法
前指针i从0开始，后指针j从n-1开始
当A[i]为偶数时，和为奇数的A[j]交换，若A[j]不为奇数，j向前移，知道A[j]为奇数再交换



#### 代码实现
```python
class Solution(object):
    def sortArrayByParity(self, A):
        """
        :type A: List[int]
        :rtype: List[int]
        """
        j = len(A)-1
        for i in range(len(A)):
            if A[i]%2!=0:
                while j>i:
                    if A[j]%2==0:
                        A[i], A[j] = A[j], A[i]
                        j -= 1
                        break
                    j -= 1
                   
        return A
        
```

本文链接：[https://www.jianshu.com/p/ff0048981995](https://www.jianshu.com/p/ff0048981995)
