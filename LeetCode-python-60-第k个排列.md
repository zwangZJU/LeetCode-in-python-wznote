 [题目链接](https://leetcode-cn.com/problems/permutation-sequence/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数学
***
给出集合 [1,2,3,…,n]，其所有元素共有 n! 种排列。

按大小顺序列出所有排列情况，并一一标记，当 n = 3 时, 所有排列如下：

"123"
"132"
"213"
"231"
"312"
"321"
给定 n 和 k，返回第 k 个排列。

**示例1**
>输入: n = 3, k = 3
输出: "213"

**示例2**
>输入: n = 4, k = 9
输出: "2314"

#### 解题思路
***
对于n个数的排列，以‘1’开头的排列有(n-1)!个，以‘2’开头的排列有(n-1)!个，等等，通过这种方式可以计算出第k个排列是由哪个数字开头的

例如：
n=3, k=3
以‘1’开头的排列有2 （由(3-1)!计算可知）个，第3个，是由‘2’开头，现在数字只剩下‘1’，‘3’
问题转化为‘1’，‘3’两个数构成的排列中，第1（由3-2得）个排列的第1个数字是多少，依次类推，确定所有数字

#### 代码实现
```
import math
class Solution:
    def getPermutation(self, n: int, k: int) -> str:
        kth = ''
        nums = list(map(str, range(1, n+1)))
        k -= 1
        while n>0:
            n -= 1
            f = math.factorial(n)
            index, k = divmod(k, f)
            kth += nums.pop(index)        
        return kth
```
