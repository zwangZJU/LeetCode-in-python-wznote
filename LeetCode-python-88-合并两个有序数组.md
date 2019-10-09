 [题目链接](https://leetcode-cn.com/problems/merge-sorted-array/)
难度： 简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组
***
给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

说明:

初始化 nums1 和 nums2 的元素数量分别为 m 和 n。
你可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。

**示例**
>输入:
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3
输出: [1,2,2,3,5,6]

#### 解题思路
***
因为两个数组都是有序的，从后往前遍历两个数组，比较大小，第i次比较时，将大的数字放在nums1的后面
1. 初始化时，$p_1 = m-1$，$p_2 = n-1$，$p_1，p_2$ 分别指向nums1，nums2的最后一位
2. 比较nums1[$p_1$]和nums2[$p_2$]的大小，第i次比较时，将更大的数字写入数组nums1的第m+n-1-i位，并且指向更大数的指针减1
3. 重复第2步直到$p_1，p_2$ 均小于0

如示例中的输入：
第1次比较：nums2[2]>nums1[2],nums1 = [1,2,3,0,0,6], 更新指针：$p_1 = 2$, $p_2= 1$
第2次比较：nums2[1]>nums1[2],nums1 = [1,2,3,0,5,6], 更新指针：$p_1 = 2$, $p_2= 0$
第3次比较：nums2[0]<nums1[2],nums1 = [1,2,3,3,5,6], 更新指针：$p_1 = 1$, $p_2= 0$
第4次比较：nums2[0]=nums1[1],nums1 = [1,2,2,3,5,6], 更新指针：$p_1 = 1$, $p_2= -1$
第5次比较：nums1 = [1,2,2,3,5,6], 更新指针：$p_1 = 0$, $p_2= -1$
第6次比较：nums1 = [1,2,2,3,5,6], 更新指针：$p_1 = -1$, $p_2= -1$

#### 代码实现
```
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: None Do not return anything, modify nums1 in-place instead.
        """
        curr = n+m-1
        if m == 0:
            for i in range(curr+1):
                nums1[i] = nums2[i]
            
            n = 0
        while m>0 or n>0:
            a = nums2[n-1] if n-1>=0 else nums1[0]-1
            b = nums1[m-1] if m-1>=0 else nums2[0]-1
            if a>b:
                nums1[curr] = a
                n -= 1
            else:
                nums1[curr] = b
                m -= 1
            curr -= 1
```

本文链接：[https://www.jianshu.com/p/c98bed924a47](https://www.jianshu.com/p/c98bed924a47)
