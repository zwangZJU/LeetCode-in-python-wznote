 [题目链接](https://leetcode-cn.com/problems/majority-element-ii/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给定一个大小为 n 的数组，找出其中所有出现超过 ⌊ n/3 ⌋ 次的元素。

说明: 要求算法的时间复杂度为 O(n)，空间复杂度为 O(1)。

 
**示例1**
> 输入: [3,2,3]
输出: [3]

**示例2**
> 输入: [1,1,1,3,3,2,2,2]
输出: [1,2]

#### 解题思路
***
 投票法
超过n/3的数最多只能有两个，选两个候选人a,b，每个候选人的表示方法为[数值，票数]
遍历数组
- 当前元素为a时，a的票数+1
- 当前元素为b时，b的票数+1
- 当前元素既不等于a也不等于b时：
-- 如果当前有候选人票数为0，新元素上位，票数更新为1
-- 如果当前所有候选人票数都大于0，a,b两人票数均-1




#### 代码实现
```python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: List[int]
        """
        candidate1 = [0, 0]
        candidate2 = [0, 0]
        for n in nums:
            if n == candidate1[0]:
                candidate1[1] += 1
            elif n == candidate2[0]:
                candidate2[1] += 1
            elif candidate1[1] == 0:
                candidate1 = [n, 1]
            elif candidate2[1] == 0:
                candidate2 = [n, 1]
            else:
                candidate1[1] -= 1
                candidate2[1] -= 1
            
        return [x for x in set([candidate1[0], candidate2[0]]) if nums.count(x) > len(nums)/3]
```
本文链接：[https://www.jianshu.com/p/f428ba92ca0c](https://www.jianshu.com/p/f428ba92ca0c)

 
