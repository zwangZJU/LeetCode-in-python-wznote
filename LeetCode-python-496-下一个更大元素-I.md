 [题目链接](https://leetcode-cn.com/problems/next-greater-element-i/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  栈
***
 给定两个没有重复元素的数组 nums1 和 nums2 ，其中nums1 是 nums2 的子集。找到 nums1 中每个元素在 nums2 中的下一个比其大的值。

nums1 中数字 x 的下一个更大元素是指 x 在 nums2 中对应位置的右边的第一个比 x 大的元素。如果不存在，对应位置输出-1。
 
 
**示例1**
> 输入: nums1 = [4,1,2], nums2 = [1,3,4,2].
输出: [-1,3,-1]
解释:
    对于num1中的数字4，你无法在第二个数组中找到下一个更大的数字，因此输出 -1。
    对于num1中的数字1，第二个数组中数字1右边的下一个较大数字是 3。
    对于num1中的数字2，第二个数组中没有下一个更大的数字，因此输出 -1。

**示例2**
> 输入: nums1 = [2,4], nums2 = [1,2,3,4].
输出: [3,-1]
解释:
    对于num1中的数字2，第二个数组中的下一个较大数字是3。
    对于num1中的数字4，第二个数组中没有下一个更大的数字，因此输出 -1。

 
#### 解题思路
***
遍历nums数组，
1.当stack为空或者当前元素小于栈顶元素时，该数进栈
2.当前元素大于栈顶元素时，栈顶元素出栈，该元素为栈顶元素的下一个更大元素，用字典保存，继续和栈顶元素比较，直到1的情况，进行1的操作
3.遍历findNums，找出该元素在字典中对应的值，若不在字典中，用-1代替，存入结果数组



#### 代码实现
```python
class Solution(object):
    def nextGreaterElement(self, findNums, nums):
        """
        :type findNums: List[int]
        :type nums: List[int]
        :rtype: List[int]
        """
        st = []
        dic = {}        
        for num in nums:
            while len(st) and st[-1]<num:
                dic[st.pop()] = num
            st.append(num)
        return [dic.get(x,-1) for x in findNums]
```

本文链接：[https://www.jianshu.com/p/99f36fcf9983](https://www.jianshu.com/p/99f36fcf9983)
