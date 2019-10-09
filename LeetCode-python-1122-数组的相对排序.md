 [题目链接](https://leetcode-cn.com/problems/relative-sort-array/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 给你两个数组，arr1 和 arr2，

arr2 中的元素各不相同
arr2 中的每个元素都出现在 arr1 中
对 arr1 中的元素进行排序，使 arr1 中项的相对顺序和 arr2 中的相对顺序相同。未在 arr2 中出现过的元素需要按照升序放在 arr1 的末尾。
 
**示例**
>输入：arr1 = [2,3,1,3,2,4,6,7,9,2,19], arr2 = [2,1,4,3,9,6]
输出：[2,2,2,1,4,3,3,9,6,7,19]

  
#### 解题思路
***
1. 统计每个数字的个数
2. 把在arr2存在的数字i按arr2中的顺序依次放到结果res中,放置k个，k为数字i在arr1中的个数
3. 把不在arr2中的数字按升序排列，接在res后面

用collections.Counter()统计字符个数，del可以删除Counter中的元素



#### 代码实现
```python
from collections import Counter
class Solution(object):
    def relativeSortArray(self, arr1, arr2):
        """
        :type arr1: List[int]
        :type arr2: List[int]
        :rtype: List[int]
        """
        
        arr1 = Counter(arr1)
        res = []
        for num in arr2:
            res.extend([num]*arr1[num])
            del arr1[num]
        res.extend(sorted(arr1.elements()))
        return res    
```

本文链接：[https://www.jianshu.com/p/7bd1df30547e](https://www.jianshu.com/p/7bd1df30547e)
