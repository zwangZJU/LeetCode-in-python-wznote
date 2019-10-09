 [题目链接](https://leetcode-cn.com/problems/longest-harmonious-subsequence/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 和谐数组是指一个数组里元素的最大值和最小值之间的差别正好是1。

现在，给定一个整数数组，你需要在所有可能的子序列中找到最长的和谐子序列的长度。

 
**示例**
> 输入: [1,3,2,2,5,2,3,7]
输出: 5
原因: 最长的和谐数组是：[3,2,2,2,3].

#### 解题思路
***
 统计每个数字的个数，用哈希表保存，其中key是i，value是i的个数
遍历哈希表，找出i和i+1最多的个数，其中i在哈希表中，当i+1不在哈希表时，该组合的总个数为0



#### 代码实现
```python
from collections import Counter
class Solution:
    def findLHS(self, nums: List[int]) -> int:
        nums = Counter(nums)
        max_len = 0
        for i in nums:
            max_len = max(max_len, nums[i]+nums[i+1] if nums[i+1] else 0)
        return max_len
```

本文链接：[https://www.jianshu.com/p/ffb9ef8bee53](https://www.jianshu.com/p/ffb9ef8bee53)
