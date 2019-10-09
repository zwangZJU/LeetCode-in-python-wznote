 [题目链接](https://leetcode-cn.com/problems/binary-prefix-divisible-by-5/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、数学
***
 给定由若干 0 和 1 组成的数组 A。我们定义 N_i：从 A[0] 到 A[i] 的第 i 个子数组被解释为一个二进制数（从最高有效位到最低有效位）。

返回布尔值列表 answer，只有当 N_i 可以被 5 整除时，答案 answer[i] 为 true，否则为 false。
 
 
**示例1**
> 输入：[0,1,1]
输出：[true,false,false]
解释：
输入数字为 0, 01, 011；也就是十进制中的 0, 1, 3 。只有第一个数可以被 5 整除，因此 answer[0] 为真。

**示例2**
>输入：[1,1,1]
输出：[false,false,false]

**示例3**
>输入：[0,1,1,1,1,1]
输出：[true,false,false,false,true,false]

**示例4**
>输入：[1,1,1,0,1]
输出：[false,false,false,false,false]

#### 解题思路
***
1.只有末尾是0或5时才能被5整除
2.每增加一位，相当于之前的所有为向右移动一位，相当于增加了2倍，再加上当前位就是当前数的大小
3.十位及以上并不影响结果，只有个位影响



#### 代码实现
```python
class Solution:
    def prefixesDivBy5(self, A: List[int]) -> List[bool]:
        for i in range(1, len(A)):
            A[i] += A[i - 1] * 2 % 5
        return [a % 5 == 0 for a in A]
```

本文链接：[https://www.jianshu.com/p/2537e2a658b0](https://www.jianshu.com/p/2537e2a658b0)
