 [题目链接](https://leetcode-cn.com/problems/top-k-frequent-elements/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 给定一个非空的整数数组，返回其中出现频率前 k 高的元素。

 说明：

你可以假设给定的 k 总是合理的，且 1 ≤ k ≤ 数组中不相同的元素的个数。
你的算法的时间复杂度必须优于 O(n log n) , n 是数组的大小。


**示例1**
> 输入: nums = [1,1,1,2,2,3], k = 2
输出: [1,2]

**示例2**
>输入: nums = [1], k = 1
输出: [1]

#### 解题思路
***
1. 用collections的Counter来统计每个元素出现的次数
2. 构建k个节点的最小堆，以元素出现的频率作为比较依据。
遍历所有元素，规则如下：
- 若堆未满，元素入堆
- 若堆满了，且当前元素的频率大于堆顶元素的频率，堆顶元素出堆，该元素入堆。
- 若堆满了，当前元素的频率小于堆顶元素，不管它
元素入堆的时间复杂度为O(log k)

使用heapq库中的 nlargest，可以在相同时间内完成，但只需要一行代码解决。



#### 代码实现
```python
class Solution:
    def topKFrequent(self, nums, k):
        """
        :type nums: List[int]
        :type k: int
        :rtype: List[int]
        """ 
        count = collections.Counter(nums)   
        return heapq.nlargest(k, count.keys(), key=count.get) 

```

本文链接：[https://www.jianshu.com/p/e6774156e902](https://www.jianshu.com/p/e6774156e902)
