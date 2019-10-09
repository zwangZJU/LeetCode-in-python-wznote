 [题目链接](https://leetcode-cn.com/problems/move-zeroes/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 数组 
***
 给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

 
**示例**
> 输入: [0,1,0,3,12]
输出: [1,3,12,0,0]

说明:

必须在原数组上操作，不能拷贝额外的数组。
尽量减少操作次数。

#### 解题思路
***
本题难点在于保持非零元素的相对顺序

 快慢指针
初始化时，快指针指向第1个位置，慢指针指向第0个位置
当慢指针指向的值不为0，快慢指针同时向前移动1
当慢指针指向的值为0时，若快指针指向的值不为0，直接交换，否则，快指针向前移动直到指向的值不为0，再交换


#### 代码实现
```python
class Solution(object):
    def moveZeroes(self, nums):
        """
        :type nums: List[int]
        :rtype: None Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        if n<2:
            return
        fast, slow = 1, 0
        while fast<n:
            if nums[slow]==0:
                while nums[fast]==0:
                    fast += 1
                    if fast>=len(nums):
                        return        
                nums[slow], nums[fast] = nums[fast], nums[slow]
            slow += 1
            if slow >=fast:
                fast = slow+1
```
本文链接：[https://www.jianshu.com/p/ca2f9c6f185b](https://www.jianshu.com/p/ca2f9c6f185b)

 
