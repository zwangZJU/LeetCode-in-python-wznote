 [题目链接](https://leetcode-cn.com/problems/daily-temperatures/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 根据每日 气温 列表，请重新生成一个列表，对应位置的输入是你需要再等待多久温度才会升高超过该日的天数。如果之后都不会升高，请在该位置用 0 来代替。


 
**示例**
> 给定一个列表 temperatures = [73, 74, 75, 71, 69, 72, 76, 73]，你的输出应该是 [1, 1, 4, 2, 1, 1, 0, 0]。
提示：气温 列表长度的范围是 [1, 30000]。每个气温的值的均为华氏度，都是在 [30, 100] 范围内的整数。

#### 解题思路
***
思路和[LeetCode-python 503.下一个更大元素 II](https://www.jianshu.com/p/4f9ef9b593f6)一致，只是这里求的是下标的距离，而不是数值
倒序搜索，用到栈，栈里存储索引
情况1：若栈为空，说明后面没有更高的温度，距离为0
情况2：若第i个元素小于栈顶索引指向的元素，距离为栈顶索引-i，之后i进栈
情况3：若第i个元素大于等于栈顶索引指向的元素，栈顶索引出栈，直到出现情况1或情况2


#### 代码实现
```python
class Solution(object):
    def dailyTemperatures(self, T):
        """
        :type T: List[int]
        :rtype: List[int]
        """
        n = len(T)
        res = [0] *n
        stack = [n-1]
        for i in range(n-2, -1, -1):
            while stack and T[i]>=T[stack[-1]]:
                stack.pop()
            res[i] = stack[-1]-i if stack else 0
            stack.append(i)
        return res
```

本文链接：[https://www.jianshu.com/p/f2690823ca7d](https://www.jianshu.com/p/f2690823ca7d)
