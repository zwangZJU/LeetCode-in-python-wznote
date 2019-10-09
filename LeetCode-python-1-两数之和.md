 [题目链接](https://leetcode-cn.com/problems/two-sum/)

难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  哈希表
***
 给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。
 
**示例**
> 给定 nums = [2, 7, 11, 15], target = 9
因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

#### 解题思路
***
 用字典保存遍历过的数字和下标
寻找target-nums[i]是否在字典中出现过，是则返回两数的下标
否则存入nums[i]及其下标



#### 代码实现
```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        dict = {}
        for i in range(len(nums)):
            if target-nums[i] in dict:
                return [dict[target-nums[i]], i]
            else:
                dict[nums[i]] = i
```

 
 本文链接：[https://www.jianshu.com/p/d922aa13637c](https://www.jianshu.com/p/d922aa13637c）
