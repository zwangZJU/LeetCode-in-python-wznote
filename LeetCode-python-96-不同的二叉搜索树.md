 [题目链接](https://leetcode-cn.com/problems/unique-binary-search-trees/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 二叉树、动态规划、卡特兰数 
***
 给定一个整数 n，求以 1 ... n 为节点组成的二叉搜索树有多少种？

 
**示例**
> 输入: 3
输出: 5
解释:
给定 n = 3, 一共有 5 种不同结构的二叉搜索树
 
 
#### 解题思路
***
 dp[i]表示i个数能组成的二叉搜索树的种数，f[i]表示以i为根结点时的二叉搜索树的种树
dp[i] = f[1]+ f[2]+ f[3]+...+ f[n]
当 i 为根节点时，其左子树节点个数为 i-1个，右子树节点个数为 n-i，则有
f[i] = dp[i-1] * dp[n-i]
可以发现，dp[i]和序列的内容无关，只与序列的长度有关

综上，dp[n] = dp[0]*dp[n-1] + dp[1]*dp[n-2]+...+dp[n-1]*dp[0]，即卡特兰数
递推公式：
dp[0] = 1 
dp[n] = $\frac{2(2n-1)/(n+2)}{n+2}$ dp[n-1]


#### 代码实现
```python
class Solution(object):
    def numTrees(self, n):
        """
        :type n: int
        :rtype: int
        """
        dp = [0] * (n+1)
        dp[0] = dp[1] = 1
        for i in range(2, n+1):
            for j in range(i+1):
                dp[i] += dp[j-1] * dp[i-j]
        return dp[n]
```

本文链接：[https://www.jianshu.com/p/d86700f0fb78](https://www.jianshu.com/p/d86700f0fb78)
