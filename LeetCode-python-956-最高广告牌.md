 [题目链接](https://leetcode-cn.com/problems/tallest-billboard/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
 你正在安装一个广告牌，并希望它高度最大。这块广告牌将有两个钢制支架，两边各一个。每个钢支架的高度必须相等。

你有一堆可以焊接在一起的钢筋 rods。举个例子，如果钢筋的长度为 1、2 和 3，则可以将它们焊接在一起形成长度为 6 的支架。

返回广告牌的最大可能安装高度。如果没法安装广告牌，请返回 0。

 
**示例1**
> 输入：[1,2,3,6]
输出：6
解释：我们有两个不相交的子集 {1,2,3} 和 {6}，它们具有相同的和 sum = 6。

**示例2**
> 输入：[1,2,3,4,5,6]
输出：10
解释：我们有两个不相交的子集 {2,3,5} 和 {4,6}，它们具有相同的和 sum = 10。

**示例3**
> 输入：[1,2]
输出：0
解释：没法安装广告牌，所以返回 0。

 
#### 解题思路
***
将问题转化为求数组和为0时的组合
对任何一个数，可以用三种方式对待它，乘以1，-1或0，目标是求和为0时的最大正数和
例如，[1，2，3], 可以对1，2乘以1，3乘以-1，此时和为0， 最大正数和为1+2=3
用字典来存储每一步的结果，k:v =总和：正数和，

初始化时dp={0:0},表示和为0时的最大长度为0
遍历所有钢筋：
对每根钢筋都有三种处理方式：加，减，丢 （对应乘以1，-1或0）
如：[1,2,3]
第一步: dp={0:0, 1:1, -1:0} 
第二步: dp={0:0, 1:1, 2:2, -1:1, 3:3, -2:0, -3:0} 对第一步中的0，1，-1的基础上分别进行“加，减，丢 ”的操作
0+2 = 2， 0-2=-2， 
1+2=3， 1-2=-1， 
-1+2=1， -1-2=-3
总和为1时，相比第一步时的正数和为1，第二步时正数和变为了2，将dp[1]修改为更大的2
总和为-1时，相比第一步时的正数和为0，第二步时正数和变为了1，将dp[-1]修改为更大的1
最后返回dp[0]

#### 代码实现
```python
class Solution(object):
    def tallestBillboard(self, rods):
        """
        :type rods: List[int]
        :rtype: int
        """
        dp = {0:0}
        for r in rods:
            for pre_sum, pos_sum in dp.items():
                dp[pre_sum-r] = max(dp.get(pre_sum-r, 0), pos_sum)               
                dp[pre_sum + r] = max(dp.get(pre_sum+r,0), pos_sum+r)
        return dp[0]
```

本文链接：[https://www.jianshu.com/p/fffe353d45c7](https://www.jianshu.com/p/fffe353d45c7)
