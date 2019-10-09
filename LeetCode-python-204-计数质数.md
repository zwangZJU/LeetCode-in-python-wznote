 [题目链接](https://leetcode-cn.com/problems/count-primes/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 数组
***
 统计所有小于非负整数 n 的质数的数量。

 
**示例**
> 输入: 10
输出: 4
解释: 小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。

#### 解题思路
***
设置一个长度为n的数组 is_primes，用于记录i是否为质数，若是，is_primes[i]=True,反之为False
遍历1到n的数，当is_primes[i]是质数是，将i的倍数位全部置False，例如：
当i=2为质数，就将4，6，8...全部修改为False
最终记录is_primes中为True的个数即可



#### 代码实现
```
class Solution:
    def countPrimes(self, n: int) -> int:
        if n<2:
            return 0
        nums = list(range(n+1))
        is_primes = [True] * n
        counter = 0
        for i in range(2,n):
            if is_primes[i]:
                counter += 1
                is_primes[i*i:n:i] = [False] * len( is_primes[i * i: n: i])
        return counter
```

本文链接：[https://www.jianshu.com/p/c252d98448cc](https://www.jianshu.com/p/c252d98448cc)
