 [题目链接](https://leetcode-cn.com/problems/pascals-triangle/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。

 
**示例**
```
输入: 5
输出:
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

#### 解题思路
***
 杨辉三角的规律是某元素的值等于其肩上量元素值的和

有个巧妙的解法：
第三行为：1，3， 3， 1
第四行为：1， 4， 6， 4， 1
恰好有：
```
  0 1 3 3 1
+ 1 3 3 1 0
= 1 4 6 4 1
```
即分别首位添0，末位添0后对应位相加

#### 代码实现
```python
class Solution(object):
    def generate(self, numRows):
        """
        :type numRows: int
        :rtype: List[List[int]]
        """
        res = [[1]]
        for i in range(1, numRows):
            res += [map(lambda x, y: x+y, res[-1] + [0], [0] + res[-1])]
        return res[:numRows]
```
本文链接：[https://www.jianshu.com/p/6adb78f48c38](https://www.jianshu.com/p/6adb78f48c38)

 
