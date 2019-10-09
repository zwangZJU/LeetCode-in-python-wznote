 [题目链接](https://leetcode-cn.com/problems/container-with-most-water/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、双指针
***
 给定 n 个非负整数 a1，a2，...，an，每个数代表坐标中的一个点 (i, ai) 。在坐标内画 n 条垂直线，垂直线 i 的两个端点分别为 (i, ai) 和 (i, 0)。找出其中的两条线，使得它们与 x 轴共同构成的容器可以容纳最多的水。

 
**示例**
>输入: [1,8,6,2,5,4,8,3,7]
输出: 49 
 
#### 解题思路
***
 这种方法背后的思路在于，两线段之间形成的区域总是会受到其中较短那条长度的限制。此外，两线段距离越远，得到的面积就越大。

我们在由线段长度构成的数组中使用两个指针，一个放在开始，一个置于末尾。 此外，我们会使用变量 maxarea 来持续存储到目前为止所获得的最大面积。 在每一步中，我们会找出指针所指向的两条线段形成的区域，更新 maxarea，并将指向较短线段的指针向较长线段那端移动一步。
 
#### 代码实现
```python
class Solution(object):
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        start = 0
        end = len(height)-1
        max_val = 0
        while start<end:
            max_val = max(max_val, (end-start)*min(height[start], height[end]))
            if height[start]>height[end]:
                end -= 1
            else:
                start += 1
        return max_val
            
```

本文链接：[https://www.jianshu.com/p/fc0186deeb72](https://www.jianshu.com/p/fc0186deeb72)
