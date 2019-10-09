 [题目链接](https://leetcode-cn.com/problems/minimum-window-substring/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串、双指针
***
 给你一个字符串 S、一个字符串 T，请在字符串 S 里面找出：包含 T 所有字母的最小子串。

 
**示例**
> 输入: S = "ADOBECODEBANC", T = "ABC"
输出: "BANC"
#### 解题思路
***
 双指针
1.用need = Counter(t)计数t中的字符以及个数，用missing计数未覆盖的字符个数
2.移动右指针,当遇到t中的字符，need对应的字符个数减一，若个数大于0，missing-=1，否则不变
3.当missing==0时，计算最小的子串
4.移动左指针，进行第3步，直到missing不等于0，进行第2步

如示例中，
1. need = {'A':1,'B':1,'C':1}, missing = 3
2. right从0开始向右移动:
right = 0时，need={'A':0,'B':1,'C':1}, missing = 2，A的个数-1
right = 1时，need={'A':0,'B':1,'C':1}, missing = 2，不变
right = 2时，need={'A':0,'B':1,'C':1}, missing = 2，不变
right = 3时，need={'A':0,'B':0,'C':1}, missing = 1，B的个数-1
right = 4时，need={'A':0,'B':1,'C':1}, missing = 1，不变
right = 5时，need={'A':0,'B':0,'C':0}, missing = 0，c的个数-1
此时最小字串为ADOBEC
3. 开始移动左指针
left指向1，need={'A':1,'B':0,'C':0}, missing = 1，A的个数+1, missing+1, 进行第二步，开始移动右指针
 

#### 代码实现
```python
import collections
class Solution(object):
    def minWindow(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: str
        """
        need = collections.Counter(t)          
        missing = len(t)                         
        start, end = 0, 0
        left = 0
        for right, char in enumerate(s, 1):           
            if need[char] > 0:
                missing -= 1
            need[char] -= 1
            if missing == 0:                     
                while left < right and need[s[left]] < 0:   
                    need[s[left]] += 1
                    left += 1
                need[s[left]] += 1                  
                missing += 1                      
                if end == 0 or right-left < end-start:   
                    start, end = left, right
                left += 1                           
        return s[start:end]
```

本文链接：[https://www.jianshu.com/p/8d91160be667](https://www.jianshu.com/p/8d91160be667)
