 [题目链接](https://leetcode-cn.com/problems/previous-permutation-with-one-swap/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  贪心算法
***
 给定两个整数 A 和 B，返回任意字符串 S，要求满足：

S 的长度为 A + B，且正好包含 A 个 'a' 字母与 B 个 'b' 字母；
子串 'aaa' 没有出现在 S 中；
子串 'bbb' 没有出现在 S 中。
 
**示例1**
> 输入：A = 1, B = 2
输出："abb"
解释："abb", "bab" 和 "bba" 都是正确答案。

**示例2**
> 输入：A = 4, B = 1
输出："aabaa"
#### 解题思路
***
 若A=B，最简单的就是a和b交替拼接
若A>B，可以用aab的形式用掉多出来的a，剩下的用ab拼接，若b用光了，剩下的用a拼接
若B>A，刚好和A>B相反



#### 代码实现
```python
class Solution(object):
    def strWithout3a3b(self, A, B):
        """
        :type A: int
        :type B: int
        :rtype: str
        """
        
        if A > B:          
            k = min(A-B, B)
            return 'aab'*k + 'ab'*(B-k)+'a'*(A-k-B) 
        else:
            k = min(B-A, A)
            return 'bba'*k + 'ba'*(A-k)+'b'*(B-k-A) 
```

本文链接：[https://www.jianshu.com/p/271a66295bd9](https://www.jianshu.com/p/271a66295bd9)
