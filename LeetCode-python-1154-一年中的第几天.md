 [题目链接](https://leetcode-cn.com/problems/ordinal-number-of-date/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数学
***
 给你一个按 YYYY-MM-DD 格式表示日期的字符串 date，请你计算并返回该日期是当年的第几天。

通常情况下，我们认为 1 月 1 日是每年的第 1 天，1 月 2 日是每年的第 2 天，依此类推。每个月的天数与现行公元纪年法（格里高利历）一致。

**示例1**
> 输入：date = "2019-01-09"
输出：9

**示例2**
> 输入：date = "2019-02-10"
输出：41

**示例3**
> 输入：date = "2003-03-01"
输出：60

**示例4**
> 输入：date = "2004-03-01"
输出：61

#### 解题思路
***
 主要分辨一下平年还是闰年：
现行公历中每400年有97个闰年。按照每四年一个闰年计算，平均每年就要多算出0.0078天，这样经过四百年就会多算出大约3天来。因此每四百年中要减少三个闰年。所以公历规定：年份是整百数时，必须是400的倍数才是闰年；不是400的倍数的世纪年，即使是4的倍数也不是闰年。



#### 代码实现
```python
class Solution(object):
    def dayOfYear(self, date):
        """
        :type date: str
        :rtype: int
        """
        y, m, d = map(int,date.split('-'))
        month = [0, 31, 29, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31]
        if y%4 != 0:
            month[2] = 28
        elif y%100==0 and y%400 != 0:
            month[2] = 28           
        return sum(month[:m])+d
```

本文链接：[https://www.jianshu.com/p/651e89d8d587](https://www.jianshu.com/p/651e89d8d587)
