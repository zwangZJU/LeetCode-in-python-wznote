 [题目链接](https://leetcode-cn.com/problems/boats-to-save-people/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  双指针、贪心算法
***
 第 i 个人的体重为 people[i]，每艘船可以承载的最大重量为 limit。

每艘船最多可同时载两人，但条件是这些人的重量之和最多为 limit。

返回载到每一个人所需的最小船数。(保证每个人都能被船载)。
 
**示例1**
> 输入：people = [1,2], limit = 3
输出：1
解释：1 艘船载 (1, 2)

**示例2**
>输入：people = [3,2,2,1], limit = 3
输出：3
解释：3 艘船分别载 (1, 2), (2) 和 (3)

**示例3**
>输入：people = [3,5,3,4], limit = 5
输出：4
解释：4 艘船分别载 (3), (3), (4), (5)

#### 解题思路
***
1. 先排序
2. 贪心：尽可能多的让船载两个人。如果最轻的人可以与任何人配对，那么让他们与最重的人配对。
如果最重的人可以与最轻的人共用一艘船，那么就这样安排。否则，最重的人无法与任何人配对，那么他们将自己独自乘一艘船。
双指针：i指向当前最轻的人，j指向当前最重的人，如果两个人能公用一条船，则有people[i]+people[j]<=limit，否则让最重的人自己坐船


#### 代码实现
```python
class Solution(object):
    def numRescueBoats(self, people, limit):
        """
        :type people: List[int]
        :type limit: int
        :rtype: int
        """
        people.sort()
        i, j = 0, len(people)-1
        res = 0
        while i<=j:
            res += 1
            if people[i]+people[j]<=limit:
                i += 1
            j -= 1
        return res
```

本文链接：[https://www.jianshu.com/p/a9ff4759eb5c](https://www.jianshu.com/p/a9ff4759eb5c)
