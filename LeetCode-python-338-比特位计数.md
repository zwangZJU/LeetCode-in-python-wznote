 [题目链接](https://leetcode-cn.com/problems/counting-bits/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 数学
***
 给定一个非负整数 num。对于 0 ≤ i ≤ num 范围中的每个数字 i ，计算其二进制数中的 1 的数目并将它们作为数组返回。


**示例1**
>输入: 2
输出: [0,1,1]

**示例2**
>输入: 5
输出: [0,1,1,2,1,2]

#### 解题思路
***
当n=10时，输出[0,1,1,2,1,2,2,3,1,2,2]
每到$2^k$时，1的个数重新变回1
$0$到$2^{k-2}$之间的数和$2^{k-1}$到$2^{k-2}$之间的数的个数相同，1的个数之差1，即首位的1。
如，3 的二进制形式是011
11的二进制形式是1011
只差首位的一个1

#### 代码实现
```
class Solution:
    def countBits(self, num: int) -> List[int]:
        res = [0]
        if num > 0:             
            while len(res) < num + 1:
                res.extend([x+1 for x in res])
        return res[:num+1]
```

本文链接：[https://www.jianshu.com/p/21785e811e62](https://www.jianshu.com/p/21785e811e62)
