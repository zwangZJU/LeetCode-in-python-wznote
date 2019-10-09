 [题目链接](https://leetcode-cn.com/problems/numbers-with-same-consecutive-differences/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 返回所有长度为 N 且满足其每两个连续位上的数字之间的差的绝对值为 K 的非负整数。

请注意，除了数字 0 本身之外，答案中的每个数字都不能有前导零。例如，01 因为有一个前导零，所以是无效的；但 0 是有效的。

你可以按任何顺序返回答案。

 

 
**示例1**
> 输入：N = 3, K = 7
输出：[181,292,707,818,929]
解释：注意，070 不是一个有效的数字，因为它有前导零。

**示例2**
> 输入：N = 2, K = 1
输出：[10,12,21,23,32,34,43,45,54,56,65,67,76,78,87,89,98]

#### 解题思路
***
如果N=1，返回0到9
如果N>1， 第一位数可以是1到9，一位一位增加，下一位可以是当前位-K或者当前位+K，只要在0到9之间即可



#### 代码实现
方法1
```python
class Solution(object):
    def numsSameConsecDiff(self, N, K):
        """
        :type N: int
        :type K: int
        :rtype: List[int]
        """
        if N==1:
            return list(range(10))
        res = list(map(str,range(1, 10)))
        for i in range(N-1):
            t = []
            for x in res:
                a = int(x[-1])
                if a-K>=0:
                    t.append(x+str(a-K))
                if a+K<=9 and K!=0:
                    t.append(x+str(a+K))
            res = t
        return [int(i) for i in res]
                
```
方法2：
```python
class Solution(object):
    def numsSameConsecDiff(self, N, K):
        """
        :type N: int
        :type K: int
        :rtype: List[int]
        """
        cur = range(10)
        for i in range(N - 1):
            cur = [x * 10 + y for x in cur for y in set([x % 10 + K, x % 10 - K]) if x and 0 <= y < 10]
        return cur
```

本文链接：[https://www.jianshu.com/p/c1b32934f6e6](https://www.jianshu.com/p/c1b32934f6e6)
