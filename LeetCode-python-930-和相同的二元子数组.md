 [题目链接](https://leetcode-cn.com/problems/binary-subarrays-with-sum/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、前缀和
***

在由若干 0 和 1  组成的数组 A 中，有多少个和为 S 的非空子数组。
 
**示例**
> 输入：A = [1,0,1,0,1], S = 2
输出：4
解释：
如下面黑体所示，有 4 个满足题目要求的子数组：
[1,0,1,0,1]
[1,0,1,0,1]
[1,0,1,0,1]
[1,0,1,0,1]
  
提示：
A.length <= 30000
0 <= S <= A.length
A[i] 为 0 或 1

#### 解题思路
***
 思路很像[LeetCode-python 560.和为K的子数组](https://www.jianshu.com/p/a634f3238eb8)
由于只有0和1，可以用数组代替字典
pre_sum[i]表示和为i的前缀的个数



#### 代码实现
```python
class Solution(object):
    def numSubarraysWithSum(self, A, S):
        """
        :type A: List[int]
        :type S: int
        :rtype: int
        """
        pre_sum = [0]*(len(A)+1)
        pre_sum[0] = 1
        cur_sum = 0
        res = 0
        for num in A:
            cur_sum += num
            if pre_sum[cur_sum - S]:
                res += pre_sum[cur_sum - S]
            pre_sum[cur_sum] += 1
        return res
```

本文链接：[https://www.jianshu.com/p/2efa08876465](https://www.jianshu.com/p/2efa08876465)
