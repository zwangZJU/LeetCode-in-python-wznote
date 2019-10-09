 [题目链接](https://leetcode-cn.com/problems/maximum-gap/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  桶排序
***
 给定一个无序的数组，找出数组在排序之后，相邻元素之间最大的差值。

如果数组元素个数小于 2，则返回 0。

 
**示例1**
> 输入: [3,6,9,1]
输出: 3
解释: 排序后的数组是 [1,3,6,9], 其中相邻元素 (3,6) 和 (6,9) 之间都存在最大差值 3。

**示例2**
>输入: [10]
输出: 0
解释: 数组元素个数小于 2，因此返回 0。

#### 解题思路
***
1. 找出数组得最大值max_val和最小值min_val
2. 每个桶的宽度为size=（max_val-min_val)/(n-1)，并向上取整，一共n+1个桶，最后一个桶存最大值，n个数放在n+1个桶，必然存在空桶，最大间距必然不来自同一个桶
3. 把每个数都放进各自的桶里，nums[i]应该放在第(nums[i]-min_val)//size个桶里，每个桶只存储该桶内的最小值和最大值，格式为[min,max]
4. 排除掉空桶后，求相邻两个桶内数字的最大距离，即第i个桶的最小值和第i-1个桶的最大值之间的差

![](https://upload-images.jianshu.io/upload_images/15048949-5e537a52c068c575.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
图片来源于[https://blog.csdn.net/zxzxzx0119/article/details/82889998](https://blog.csdn.net/zxzxzx0119/article/details/82889998)



#### 代码实现
```python
 class Solution:
    def maximumGap(self, nums):
        if len(nums) < 2:
            return 0
        max_val, min_val = max(nums), min(nums)
        if max_val == min_val:
            return 0
        n = len(nums)
        size = math.ceil((max_val-min_val)/(n-1))
         
        bucket = [[None, None] for _ in range(n+1)]
        for num in nums:
            b = bucket[(num-min_val)//size]
            b[0] = min(b[0], num) if b[0] else num
            b[1] = max(b[1], num) if b[1] else num
        bucket = [b for b in bucket if b[0] is not None]
        return max(bucket[i][0]-bucket[i-1][1] for i in range(1, len(bucket)))
```

本文链接：[https://www.jianshu.com/p/dbb8056344ea](https://www.jianshu.com/p/dbb8056344ea)
