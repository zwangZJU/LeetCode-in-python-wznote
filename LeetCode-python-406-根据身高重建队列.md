 [题目链接](https://leetcode-cn.com/problems/queue-reconstruction-by-height/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 假设有打乱顺序的一群人站成一个队列。 每个人由一个整数对(h, k)表示，其中h是这个人的身高，k是排在这个人前面且身高大于或等于h的人数。 编写一个算法来重建这个队列。

注意：
总人数少于1100人。

 
**示例**
> 输入:
[[7,0], [4,4], [7,1], [5,0], [6,1], [5,2]]
输出:
[[5,0], [7,0], [5,2], [6,1], [4,4], [7,1]]

#### 解题思路
***
 1.排序：按照身高从高到低排，升高相同的按k从小到大排
2.插入：按照排序好的顺序逐个插入新数组，插入的位置按照k来插

如示例中，排序完：
[[7,0], [7,1], [6,1], [5,0], [5,2]，[4,4]]
插入的过程：
第一插：[[7,0]]
第二插：[[7,0], [7,1]]
第三插：[[7,0], [6,1],[7,1]]
第四插：[[5,0],[7,0], [6,1],[7,1]]
...
先插高的，后插矮的，即使后插的插到前面也不会有影像，因为矮


#### 代码实现
```
class Solution(object):
    def reconstructQueue(self, people):
        """
        :type people: List[List[int]]
        :rtype: List[List[int]]
        """
        people.sort(key=lambda (h, k): (-h, k))
        res = []
        for p in people:
             
            res.insert(p[1],p)
        return res
```

本文链接：[https://www.jianshu.com/p/e2612ff668fe](https://www.jianshu.com/p/e2612ff668fe)
