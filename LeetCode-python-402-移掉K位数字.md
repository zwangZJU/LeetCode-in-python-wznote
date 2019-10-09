 [题目链接](https://leetcode-cn.com/problems/remove-k-digits/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串、栈
***
 给定一个以字符串表示的非负整数 num，移除这个数中的 k 位数字，使得剩下的数字最小。

 
**示例1**
> 输入: num = "1432219", k = 3
输出: "1219"
解释: 移除掉三个数字 4, 3, 和 2 形成一个新的最小的数字 1219。

**示例2**
>输入: num = "10200", k = 1
输出: "200"
解释: 移掉首位的 1 剩下的数字为 200. 注意输出不能有任何前导零。

**示例3**
>输入: num = "10", k = 2
输出: "0"
解释: 从原数字移除所有的数字，剩余为空就是0。

#### 解题思路
***
 遍历字符串，若num[i]大于栈顶元素，则num[i]入栈
若num[i]小于栈顶元素，栈顶元素依次出栈，直到栈顶元素小于num[i]或者出栈的总次数大于k。出栈的过程就是移掉数字的过程



#### 代码实现
```
class Solution(object):
    def removeKdigits(self, num, k):
        """
        :type num: str
        :type k: int
        :rtype: str
        """        
        n = len(num)
        t = n - k
        if n == k:
            return '0'
        res = ''
        for i in range(n):             
            while k and res and res[-1]>num[i]:
                res = res[:-1] 
                k -=1
            res += num[i]          
            if k == 0:
                res += num[i+1:]
                break     
        res = res[:t]
        for i in range(len(res)):
            if res[i] != '0':
                return res[i:] if res[i:] else '0'
        return '0'
```

本文链接：[https://www.jianshu.com/p/bf950aa23be6](https://www.jianshu.com/p/bf950aa23be6)
