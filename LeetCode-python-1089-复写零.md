 [题目链接](https://leetcode-cn.com/problems/duplicate-zeros/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、栈
***
 给你一个长度固定的整数数组 arr，请你将该数组中出现的每个零都复写一遍，并将其余的元素向右平移。

注意：请不要在超过该数组长度的位置写入元素。

要求：请对输入的数组 就地 进行上述修改，不要从函数返回任何东西。

 
**示例1**
> 输入：[1,0,2,3,0,4,5,0]
输出：null
解释：调用函数后，输入的数组将被修改为：[1,0,0,2,3,0,0,4]

**示例2**
> 输入：[1,2,3]
输出：null
解释：调用函数后，输入的数组将被修改为：[1,2,3]

#### 解题思路
***
 复写0会占据下一个数字的位置，用队列记录经过的位置上的数字，写的时候从队列里取，这样比直接复制数组要省内存


#### 代码实现
```python
class Solution:
    def duplicateZeros(self, arr: List[int]) -> None:
        """
        Do not return anything, modify arr in-place instead.
        """
        i, n = 0, len(arr)
        stack = []
        while i < n:
            stack.append(arr[i])
            t = stack.pop(0)             
            if t == 0:
                arr[i] = 0
                if i+1<n:
                    stack.append(arr[i+1])
                    arr[i+1] = 0
                i+=1
            else:
                arr[i] = t
            i += 1 
```

本文链接：[https://www.jianshu.com/p/e2fef725c747](https://www.jianshu.com/p/e2fef725c747)
