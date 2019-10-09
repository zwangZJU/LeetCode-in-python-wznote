 [题目链接](https://leetcode-cn.com/problems/maximize-sum-of-array-after-k-negations/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 数组 
***
给定一个整数数组 A，我们只能用以下方法修改该数组：我们选择某个个索引 i 并将 A[i] 替换为 -A[i]，然后总共重复这个过程 K 次。（我们可以多次选择同一个索引 i。）

以这种方式修改数组后，返回数组可能的最大和。
 

 
**示例1**
> 输入：A = [4,2,3], K = 1
输出：5
解释：选择索引 (1,) ，然后 A 变为 [4,-2,3]。

**示例2**
>输入：A = [3,-1,0,2], K = 3
输出：6
解释：选择索引 (1, 2, 2) ，然后 A 变为 [3,1,0,2]。

**示例3**
>输入：A = [2,-3,-1,5,-4], K = 2
输出：13
解释：选择索引 (1, 4) ，然后 A 变为 [2,3,-1,5,4]。

#### 解题思路
***
 1.从小到大排序
2.先用取反的机会把负数变正，直到k次机会用光或者所有数都为正
3.若k次机会用光，直接求和；若没用光，说明数组a此时都是正数，若剩余的取反次数不能被2整除，必定有个数会变为负数，让数组最小值变为负求和可得到最小值，若能被2整除，直接求和



#### 代码实现
```python
class Solution:
    def largestSumAfterKNegations(self, A: List[int], K: int) -> int:
        a = sorted(A)
        i, n = 0, len(a)
        while i<n and i<K and a[i]<0:
            a[i] = -a[i]
            i += 1
        return sum(a) - (K-i)%2 *2*min(a)
```

本文链接：[https://www.jianshu.com/p/1e7c142d0cf9](https://www.jianshu.com/p/1e7c142d0cf9)
