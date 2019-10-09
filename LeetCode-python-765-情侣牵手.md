 [题目链接](https://leetcode-cn.com/problems/previous-permutation-with-one-swap/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 N 对情侣坐在连续排列的 2N 个座位上，想要牵到对方的手。 计算最少交换座位的次数，以便每对情侣可以并肩坐在一起。 一次交换可选择任意两人，让他们站起来交换座位。

人和座位用 0 到 2N-1 的整数表示，情侣们按顺序编号，第一对是 (0, 1)，第二对是 (2, 3)，以此类推，最后一对是 (2N-2, 2N-1)。

这些情侣的初始座位  row[i] 是由最初始坐在第 i 个座位上的人决定的。

 
**示例1**
> 输入: row = [0, 2, 1, 3]
输出: 1
解释: 我们只需要交换row[1]和row[2]的位置即可。

**示例2**
> 输入: row = [3, 2, 0, 1]
输出: 0
解释: 无需交换座位，所有的情侣都已经可以手牵手了。

#### 解题思路
***
 用字典记录每个编号的位置
先给0配对，再给2配对，再给4配对。。。
若0的坐标是i，i是奇数，看它前一位是不是1，若不是，就在字典找1的位置，让i-1位上的数字和1调换位置，并更新字典中的位置
若i是偶数，就看它的后一位是不是1，若不是，找，换
记录交换的次数



#### 代码实现
```python
class Solution(object):
    def minSwapsCouples(self, row):
        """
        :type row: List[int]
        :rtype: int
        """
        n_swap = 0
        place = {x:i for (i,x) in enumerate(row)}
        n = len(row)
        for i in range(0,n,2):
            x = row[i]            
            if x % 2 == 0:
                y = x + 1
            else:
                y = x - 1
            j = place[y]
                        
            if abs(i-j) > 1: 
                row[i+1], row[j] = row[j], row[i+1]
                place[row[i+1]], place[row[j]] = i+1, j              
                n_swap += 1
                
        return n_swap
```

本文链接：[https://www.jianshu.com/p/f4d7dbcb1db3](https://www.jianshu.com/p/f4d7dbcb1db3)
