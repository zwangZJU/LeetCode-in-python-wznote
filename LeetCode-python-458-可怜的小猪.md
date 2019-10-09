[题目链接](https://leetcode-cn.com/problems/nim-game/description/)
难度： 困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数学
***
有1000只水桶，其中有且只有一桶装的含有毒药，其余装的都是水。它们从外观看起来都一样。如果小猪喝了毒药，它会在15分钟内死去。

问题来了，如果需要你在一小时内，弄清楚哪只水桶含有毒药，你最少需要多少只猪？

回答这个问题，并为下列的进阶问题编写一个通用算法。

进阶:
假设有 n 只水桶，猪饮水中毒后会在 m 分钟内死亡，你需要多少猪（x）就能在 p 分钟内找出“有毒”水桶？n只水桶里有且仅有一只有毒的桶。

#### 解题思路
***
毒死一只小猪需要15分钟，一只猪在60分钟内能测试4次，若有两只猪，最多可测出25桶水中哪一桶有毒


|1| 2| 3| 4| 5|
|-|-|-|-|-|
|6| 7| 8| 9| 10|
|11| 12| 13| 14| 15|
|16| 17| 18| 19| 20|
|21| 22| 23| 24| 25|

第1只猪喝每一行所有编号的水桶的混合水，第2只猪喝每一列所有编号的水桶的混合水，如果第一只毒死在第0行，第二只没有死，则有毒的水是第5桶

如果有三只猪， 可以用类似的方法构建5x5x5的立方阵，最多可测125桶水
#### 代码实现
```
class Solution(object):
    def poorPigs(self, buckets, minutesToDie, minutesToTest):
        """
        :type buckets: int
        :type minutesToDie: int
        :type minutesToTest: int
        :rtype: int
        """
        num_pig = 0
        while (minutesToTest/minutesToDie+1)**num_pig < buckets:
            num_pig += 1
        return num_pig
```

本文链接：[https://www.jianshu.com/p/0bb457d3d797](https://www.jianshu.com/p/0bb457d3d797)
