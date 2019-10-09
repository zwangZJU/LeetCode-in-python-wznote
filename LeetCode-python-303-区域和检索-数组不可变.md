 [题目链接](https://leetcode-cn.com/problems/range-sum-query-immutable/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个整数数组  nums，求出数组从索引 i 到 j  (i ≤ j) 范围内元素的总和，包含 i,  j 两点。

 
**示例**
> 给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()
sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3

#### 解题思路
***
用另一个数组stack的第i位存储num的前i项和
第k到第j位的和为stack[j]-stack[k-1]

#### 代码实现
```python
class NumArray(object):

    def __init__(self, nums):
        """
        :type nums: List[int]
        """
        self.stack = [0]
        for n in nums:
            self.stack.append(self.stack[-1]+n)
        

    def sumRange(self, i, j):
        """
        :type i: int
        :type j: int
        :rtype: int
        """
        return self.stack[j+1]-self.stack[i]


# Your NumArray object will be instantiated and called as such:
# obj = NumArray(nums)
# param_1 = obj.sumRange(i,j)
```

本文链接：[https://www.jianshu.com/p/65441fae2c3c](https://www.jianshu.com/p/65441fae2c3c)
