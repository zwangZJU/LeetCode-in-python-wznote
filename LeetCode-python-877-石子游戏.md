 [题目链接](https://leetcode-cn.com/problems/stone-game/description/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：动态规划
***
亚历克斯和李用几堆石子在做游戏。偶数堆石子排成一行，每堆都有正整数颗石子 piles[i] 。

游戏以谁手中的石子最多来决出胜负。石子的总数是奇数，所以没有平局。

亚历克斯和李轮流进行，亚历克斯先开始。 每回合，玩家从行的开始或结束处取走整堆石头。 这种情况一直持续到没有更多的石子堆为止，此时手中石子最多的玩家获胜。

假设亚历克斯和李都发挥出最佳水平，当亚历克斯赢得比赛时返回 true ，当李赢得比赛时返回 false 。

**示例**
>输入：[5,3,4,5]
输出：true
解释：
    - 亚历克斯先开始，只能拿前 5 颗或后 5 颗石子 。
    - 假设他取了前 5 颗，这一行就变成了 [3,4,5] 。
    - 如果李拿走前 3 颗，那么剩下的是 [4,5]，亚历克斯拿走后 5 颗赢得 10 分。
    - 如果李拿走后 5 颗，那么剩下的是 [3,4]，亚历克斯拿走后 4 颗赢得 9 分。
    - 这表明，取前 5 颗石子对亚历克斯来说是一个胜利的举动，所以我们返回 true 。


#### 解题思路
***
让我们改变游戏规则，使得每当李得分时，都会从亚历克斯的分数中扣除。

令 dp(i, j) 为亚历克斯可以获得的最大分数，其中剩下的堆中的石子数是 piles[i], piles[i+1], ..., piles[j]。这在比分游戏中很自然：我们想知道游戏中每个位置的值。

我们可以根据 dp[i + 1][j] 和 dp[i][j-1] 来制定 dp[i][j] 的递归，我们可以使用动态编程以不重复这个递归中的工作。（该方法可以输出正确的答案，因为状态形成一个DAG（有向无环图）。）

#### 算法
***
当剩下的堆的石子数是 piles[i], piles[i+1], ..., piles[j] 时，轮到的玩家最多有 2 种行为。

可以通过比较 j-i和 N modulo 2 来找出轮到的人。

如果玩家是亚历克斯，那么她将取走 piles[i] 或 piles[j] 颗石子，增加她的分数。之后，总分为 piles[i] + dp[i+1][ j] 或 piles[j] + dp[i][ j-1]；我们想要其中的最大可能得分。

如果玩家是李，那么他将取走 piles[i] 或 piles[j] 颗石子，减少亚历克斯这一数量的分数。之后，总分为 -piles[i] + dp[i+1][ j] 或 -piles[j] + dp[i][j-1]；我们想要其中的最小可能得分。
 
 

#### 另一个算法
***
动态规划，建立二维数组dp[N][N],其中N为piles数组长度。
- dp[ i ][ j ]表示在piles中下标 i 至下标 j 之间的亚力克斯所拿石子总数和李所拿石子总数之差
- dp[ i ][ j ] > 0 时亚历克斯拿的石子数目大于李，亚力克斯胜利，否则李胜利
- dp的初始状态是 i = j 即只有一个石子堆，由于亚历克斯先拿，则 dp[ i ][ j ] = piles[ i ]
- 当亚历克斯拿了最左边下标为 i 的石子后，亚历克斯和李的石子数之差为 piles[ i ] - dp[ i+1 ][ j ], 当亚历克斯拿了最右边下标为j的那堆石子后，亚历克斯和李的石子数之差为 piles[ j ] - dp[ i ][ j-1 ], 取其中较大者为新的最优解。
- 动态转移方程: dp[ i ][ j ] = max( piles[ i ] - dp[ i+1 ][ j ], piles[ j ] - dp[ i ][ j-1 ])

#### 代码实现
```python
class Solution:
    def stoneGame(self, piles):
        n = len(piles)
        dp = [[0]*n for _ in range(n)]
        for i in range(n):
            dp[i][i] = piles[i]
        for left in range(n-2, -1, -1):
            for right in range(left + 1, n): 
                dp[left][right] = max(piles[left] - dp[left+1][right], piles[right] - dp[left][right-1])
        return dp[0][n-1] > 0
```

本文链接：[https://www.jianshu.com/p/35986b27b24f](https://www.jianshu.com/p/35986b27b24f)

