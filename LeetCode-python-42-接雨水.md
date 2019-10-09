 [题目链接](https://leetcode-cn.com/problems/trapping-rain-water/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  栈
***
 给定 n 个非负整数表示每个宽度为 1 的柱子的高度图，计算按此排列的柱子，下雨之后能接多少雨水。
 ![](https://upload-images.jianshu.io/upload_images/15048949-c134c64c3a85c430.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

 
**示例**
> 输入: [0,1,0,2,1,0,1,3,2,1,2,1]
输出: 6
#### 解题思路
***
图片来源于 https://leetcode-cn.com/problems/two-sum/solution/jie-yu-shui-by-leetcode/
 ![](https://upload-images.jianshu.io/upload_images/15048949-3c4e2bc176e63e2f.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
- 找到数组中从下标 i 到最左端最高的条形块高度 $\text{left_max}$。
- 找到数组中从下标 i 到最右端最高的条形块高度 $\text{right_max}$。
- 扫描数组 $\text{height} $并更新答案：
累加 $\min(\text{max_left}[i],\text{max_right}[i]) - \text{height}[i] $到 总面积上

 



#### 代码实现
```python
class Solution(object):
    def trap(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        max_left = [0]         
        for h in height:             
            max_left.append(max(max_left[-1], h))
        max_right = 0    
        res = 0
        n = len(height)
        for i in range(n):
            max_right = max(max_right, height[n-i-1])
            
            res += min(max_right, max_left[n-i]) - height[n-i-1]
        return res
```

本文链接：[https://www.jianshu.com/p/b29b12c4f7b1](https://www.jianshu.com/p/b29b12c4f7b1)
