 [题目链接](https://leetcode-cn.com/problems/sort-colors/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划
***
给定一个包含红色、白色和蓝色，一共 *n *个元素的数组，**[原地](https://baike.baidu.com/item/%E5%8E%9F%E5%9C%B0%E7%AE%97%E6%B3%95)**对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

**注意:**
不能使用代码库中的排序函数来解决这道题。

**示例**
>输入: [2,0,2,1,1,0]
输出: [0,0,1,1,2,2]

#### 解题思路
***
遍历数组，碰到0往左放，碰到2往右放
规则：
设置一个red指针，保证red指针的左侧都为0
设置一个blue指针，保证blue指针的右侧都为零
设置一个white指针，保证red到white之间都为1
初始化：
red = 0, white=0, blue=数组长度-1
更新：
white指针从0开始向右移动，white>blue时结束
    nums[white] = 0 时，和nums[red]交换， red++,  white++
    nums[white] = 2 时，和nums[blue]交换， blue--
    nums[white] = 1 时，white++

#### 代码实现
```
class Solution:
    def sortColors(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        n = len(nums)
        red, white, blue = 0, 0, n-1
        while white <= blue:
            if nums[white] == 0:
                nums[white], nums[red] = nums[red], nums[white]
                white += 1
                red += 1
            elif nums[white] == 1:
                white += 1
            else:
                nums[white], nums[blue] = nums[blue], nums[white]
                blue -= 1
```

本文链接：[https://www.jianshu.com/p/4da8fffe09be](https://www.jianshu.com/p/4da8fffe09be)
