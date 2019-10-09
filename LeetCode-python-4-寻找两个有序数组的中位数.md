 [题目链接](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)

难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 
给定两个大小为 m 和 n 的有序数组 nums1 和 nums2。

请你找出这两个有序数组的中位数，并且要求算法的时间复杂度为 O(log(m + n))。

你可以假设 nums1 和 nums2 不会同时为空。
 
**示例1**
> nums1 = [1, 3]
nums2 = [2]
则中位数是 2.0

**示例2**
>nums1 = [1, 2]
nums2 = [3, 4]
则中位数是 (2 + 3)/2 = 2.5

#### 解题思路
***
 将问题广义化为寻找两个数组中第K小的数

设两个数组num1, num2的长度分别为l1, l2
当l1+l2为奇数，k=(l1+l2)//2
当l1+l2为偶数，分别找到第(l1+l2)//2-1和第(l1+l2)//2个数求均值

如何找第k个数？
二分法，每次将两个数组分成两半，中位数分别为m1和m2,中位数的下标分别为i1和i2

- 若i1+i2<k，即第k个数一定不在某个数组的前半部分，当m1>m2时，第k个数一定不在nums2的前半部分，下一次搜索改为在nums1和nums2的后半部分里寻找第k-i2-1个数；当m1<=m2时,同理，问题变为在nums1的后半部分和nums2里寻找第k-i1-1个数

- 若i1+i2>=k，即第k个数一定不在某个数组的后半部分，当m1>m2时，第k个数一定不在nums1的后半部分，问题变为，在nums1的前半部分和nums2中寻找第k个数；反之不在nums2的后半部分，问题也相应改变，这样搜索的范围就减小了



#### 代码实现
```
class Solution(object):
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        n = len(nums1)+len(nums2)
        if n%2==1:
            return self.findKth(nums1, nums2, n//2)
        else:
            return (self.findKth(nums1, nums2, n//2)+self.findKth(nums1, nums2, n//2-1))/2
        
    def findKth(self, nums1, nums2, k):
        if not nums1:
            return nums2[k]
        if not nums2:
            return nums1[k]
        i1, i2 = len(nums1)//2, len(nums2)//2
        print(i1,i2)
        m1, m2 = nums1[i1], nums2[i2]
        
        if i1 + i2 < k:
            if m1 > m2:
                self.findKth(nums1, nums2[i2+1], k-i2-1)
            else: 
                self.findKth(nums1[i1+1:], nums2, k-i1-1)
        else:
            if m1 > m2:
                self.findKth(nums1[:i1], nums2, k)
            else:
                self.findKth(nums1, nums2[:i2], k)
```

本文链接：[https://www.jianshu.com/p/15239884df4f](https://www.jianshu.com/p/15239884df4f)
