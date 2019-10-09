 [题目链接](https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组  
***
 给定一个整数数组，你需要寻找一个连续的子数组，如果对这个子数组进行升序排序，那么整个数组都会变为升序排序。

你找到的子数组应是最短的，请输出它的长度。

 
**示例**
> 输入: [2, 6, 4, 8, 10, 9, 15]
输出: 5
解释: 你只需要对 [6, 4, 8, 10, 9] 进行升序排序，那么整个表都会变为升序排序。

 
#### 解题思路
***
 数组复制一份，排序
比较原数组与排序后数组相同位置上第一个和倒数第一个值不一样的位置



#### 代码实现
```python
class Solution:
    def findUnsortedSubarray(self, nums: List[int]) -> int:
        t = sorted(nums)
        n = len(nums)
        left, right, = 0, n-1
        while left<n:
            if t[left] != nums[left]:
                break
            left += 1
        if left == n:
            return 0
        while right>0:
            if t[right] != nums[right]:
                return right - left +1
            right -= 1
```

本文链接：[https://www.jianshu.com/p/1e4a77ca65e2](https://www.jianshu.com/p/1e4a77ca65e2)
