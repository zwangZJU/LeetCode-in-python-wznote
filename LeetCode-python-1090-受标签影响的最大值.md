 [题目链接](https://leetcode-cn.com/problems/largest-values-from-labels/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  贪心算法
***
 我们有一个项的集合，其中第 i 项的值为 values[i]，标签为 labels[i]。

我们从这些项中选出一个子集 S，这样一来：

|S| <= num_wanted
对于任意的标签 L，子集 S 中标签为 L 的项的数目总满足 <= use_limit。
返回子集 S 的最大可能的 和。

 
**示例1**
> 输入：values = [5,4,3,2,1], labels = [1,1,2,2,3], num_wanted = 3, use_limit = 1
输出：9
解释：选出的子集是第一项，第三项和第五项。

**示例2**
>输入：values = [5,4,3,2,1], labels = [1,3,3,3,2], num_wanted = 3, use_limit = 2
输出：12
解释：选出的子集是第一项，第二项和第三项。
 

**示例3**
>输入：values = [9,8,8,7,6], labels = [0,0,0,1,1], num_wanted = 3, use_limit = 1
输出：16
解释：选出的子集是第一项和第四项。
 

**示例4**
>输入：values = [9,8,8,7,6], labels = [0,0,0,1,1], num_wanted = 3, use_limit = 2
输出：24
解释：选出的子集是第一项，第二项和第四项。

 
#### 解题思路
***
 虽然受标签影响，但目的还是选最大值，先按照value从大到小排序
从大往小撸，并记录label使用的次数，如果同一label使用超过use_limit，就跳过它，否则在总和中加上它，若筛选出的总数大于num_wanted，就停止筛选



#### 代码实现
```python
class Solution(object):
    def largestValsFromLabels(self, values, labels, num_wanted, use_limit):
        """
        :type values: List[int]
        :type labels: List[int]
        :type num_wanted: int
        :type use_limit: int
        :rtype: int
        """
        nums = sorted(zip(values, labels))
         
        used = {}
        res = 0
        while num_wanted > 0 and nums:
            val, label = nums.pop()
            if used.get(label,0) < use_limit:                 
                used[label] = used.get(label, 0) + 1
                res += val
                num_wanted -= 1
                 
        return res
```

本文链接：[https://www.jianshu.com/p/3541b0bb6e98](https://www.jianshu.com/p/3541b0bb6e98)
