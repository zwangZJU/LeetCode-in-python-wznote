 [题目链接](https://leetcode-cn.com/problems/shortest-distance-to-a-character/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
给定一个字符串 S 和一个字符 C。返回一个代表字符串 S 中每个字符到字符串 S 中的字符 C 的最短距离的数组。 

 
**示例**
> 输入: S = "loveleetcode", C = 'e'
输出: [3, 2, 1, 0, 1, 0, 0, 1, 2, 2, 1, 0]

#### 解题思路
***
 初始化一维n列的全n距离矩阵res，因为最长距离不会超过n
找到S中所有等于C的字符的位置存入列表index，并将res相应位置的值修改为0
再从index中的位置开始从中心向两边扩展，求最小距离


#### 代码实现
```python
class Solution:
    def shortestToChar(self, S: str, C: str) -> List[int]:
        n, index = len(S), []         
        res = [n]*n
        for i in range(n):
            if S[i] == C:
                index.append(i)
                res[i] = 0
        for i in index:
            j = i-1
            while j>=0 and res[j]>i-j:
                res[j] = i-j
                j -= 1
            j = i+1
            while j<n and res[j]>j - i:
                res[j] = j - i
                j += 1
        return res
```

本文链接：[https://www.jianshu.com/p/3ac2c261319c](https://www.jianshu.com/p/3ac2c261319c)
