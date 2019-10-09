 [题目链接](https://leetcode-cn.com/problems/stone-game/description/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：贪心算法
***
给定两个大小相等的数组 A 和 B，A 相对于 B 的优势可以用满足 A[i] > B[i] 的索引 i 的数目来描述。

返回 A 的任意排列，使其相对于 B 的优势最大化。

**示例1**
>输入：A = [2,7,11,15], B = [1,10,4,11]
输出：[2,11,7,15]

**示例2**
>输入：A = [12,24,8,32], B = [13,25,32,11]
输出：[24,32,8,12]

#### 解题思路
***
排序A和B, 如果A中最小的数大于B中最小的数，则将A的最小数分配给B的最小数。 否则A放入remain列表中。其余的数以此类推分析。
#### 代码实现
```
class Solution(object):
    def advantageCount(self, A, B):
        sortedA = sorted(A)
        sortedB = sorted(B)

        # assigned[b] = list of a that are assigned to beat b
        # remaining = list of a that are not assigned to any b
        assigned = {b: [] for b in B} 
        remaining = []

        # populate (assigned, remaining) appropriately
        # sortedB[j] is always the smallest unassigned element in B
        j = 0
        for a in sortedA:
            if a > sortedB[j]:
                assigned[sortedB[j]].append(a)
                j += 1
            else:
                remaining.append(a)
        # Reconstruct the answer from annotations (assigned, remaining)
        return [assigned[b].pop() if assigned[b] else remaining.pop()
                for b in B]
```

本文链接：[https://www.jianshu.com/p/44f01ff86d29](https://www.jianshu.com/p/44f01ff86d29)
