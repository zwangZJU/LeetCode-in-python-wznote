 [题目链接](https://leetcode-cn.com/problems/moving-stones-until-consecutive/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 三枚石子放置在数轴上，位置分别为 a，b，c。

每一回合，我们假设这三枚石子当前分别位于位置 x, y, z 且 x < y < z。从位置 x 或者是位置 z 拿起一枚石子，并将该石子移动到某一整数位置 k 处，其中 x < k < z 且 k != y。

当你无法进行任何移动时，即，这些石子的位置连续时，游戏结束。

要使游戏结束，你可以执行的最小和最大移动次数分别是多少？ 以长度为 2 的数组形式返回答案：answer = [minimum_moves, maximum_moves]

 

 
**示例1**
> 输入：a = 1, b = 2, c = 5
输出：[1, 2]
解释：将石子从 5 移动到 4 再移动到 3，或者我们可以直接将石子移动到 3。

**示例2**
>输入：a = 4, b = 3, c = 2
输出：[0, 0]
解释：我们无法进行任何移动。
 
#### 解题思路
***
三个值先从小到大排序
 最大值：左右两端一步一步向b移动，a到c一共又c-a-2个空格
最小值：1. 如果a贴着b，a不用移动，没贴着就移动一步就可以，c同理
              2.如果a和b中间空了一格，把c一步一进去就行，c和b只空一格同理



#### 代码实现
```python
class Solution(object):
    def numMovesStones(self, a, b, c):
        """
        :type a: int
        :type b: int
        :type c: int
        :rtype: List[int]
        """
        a, b, c = sorted([a,b,c])
        max_moves = c - a -2
        min_moves = 1 if b-a==2 or c-b ==2 else min(b-a-1, 1) + min(c-b-1,1)
        return [min_moves, max_moves]
```

本文链接：[https://www.jianshu.com/p/a059ab85d960](https://www.jianshu.com/p/a059ab85d960)
