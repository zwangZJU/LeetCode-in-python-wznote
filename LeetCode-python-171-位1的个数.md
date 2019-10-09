 [题目链接](https://leetcode-cn.com/problems/number-of-1-bits/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 编写一个函数，输入是一个无符号整数，返回其二进制表达式中数字位数为 ‘1’ 的个数（也被称为[汉明重量](https://baike.baidu.com/item/%E6%B1%89%E6%98%8E%E9%87%8D%E9%87%8F)）。


 
**示例**
> 输入：00000000000000000000000000001011
输出：3
解释：输入的二进制串 00000000000000000000000000001011 中，共有三位为 '1'。

#### 解题思路
***
方法1：
 将数字转成二进制字符串，统计1的个数

方法2：
对于a=XXX100,a-1=XXX011,a&(a-1)=0
每次进行上述&操作，都能消掉最右侧的1，一直消到最左侧的1，统计消了几次即可

#### 代码实现
方法1：
```python
class Solution(object):
    def hammingWeight(self, n):
        """
        :type n: int
        :rtype: int
        """
        b = bin(n)
        res = 0
        for c in b[2:]:
            res += int(c)
        return res
```
方法2：
```python
def hammingWeight(self, n):
    """
    :type n: int
    :rtype: int
    """
    c = 0
    while n:
        n &= n - 1
        c += 1
    return c
```

本文链接：[https://www.jianshu.com/p/891fcad3dee2](https://www.jianshu.com/p/891fcad3dee2)
