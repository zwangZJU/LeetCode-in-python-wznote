 [题目链接](https://leetcode-cn.com/problems/find-k-closest-elements/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、二分查找
***
 给定一个排序好的数组，两个整数 k 和 x，从数组中找到最靠近 x（两数之差最小）的 k 个数。返回的结果必须要是按升序排好的。如果有两个数与 x 的差值一样，优先选择数值较小的那个数。

说明:
k 的值为正数，且总是小于给定排序数组的长度。
数组不为空，且长度不超过 104
数组里的每个元素与 x 的绝对值不超过 104
 

 
**示例1**
> 输入: [1,2,3,4,5], k=4, x=3
输出: [1,2,3,4]

**示例2**
>输入: [1,2,3,4,5], k=4, x=-1
输出: [1,2,3,4]

#### 解题思路
***
 二分查找找到离x最近的数，然后在附近搜索差最小的数



#### 代码实现
```
class Solution(object):
    def findClosestElements(self, arr, k, x):
        """
        :type arr: List[int]
        :type k: int
        :type x: int
        :rtype: List[int]
        """
        self.res = []
        def find(arr, left, right, k, x):
            while k>0:
                k-=1
                if left<0:
                    self.res += arr[right:right+k+1]
                    break
                elif right>=len(arr):
                    self.res = arr[left-k:left+1] + self.res 
                    break
                elif abs(arr[left]-x) <= abs(arr[right]-x):
                    self.res = [arr[left]] + self.res
                    left -= 1
                else:
                    self.res += [arr[right]]
                    right += 1
           
        
        left, right = 0, len(arr)
        while left<right:
            mid = (left+right)//2
            if arr[mid] == x:
                self.res.append(x)
                find(arr, mid-1, mid+1, k-1, x)
                return self.res
            
            elif arr[mid]>x:
                right = mid
            else:
                left = mid+1
        find(arr, left-1, right, k, x)
        return self.res
```

本文链接：[https://www.jianshu.com/p/3ed7e3cf5d38](https://www.jianshu.com/p/3ed7e3cf5d38)
