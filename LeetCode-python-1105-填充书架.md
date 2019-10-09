 [题目链接](https://leetcode-cn.com/problems/filling-bookcase-shelves/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  动态规划
***
 附近的家居城促销，你买回了一直心仪的可调节书架，打算把自己的书都整理到新的书架上。

你把要摆放的书 books 都整理好，叠成一摞：从上往下，第 i 本书的厚度为 books[i][0]，高度为 books[i][1]。

按顺序 将这些书摆放到总宽度为 shelf_width 的书架上。

先选几本书放在书架上（它们的厚度之和小于等于书架的宽度 shelf_width），然后再建一层书架。重复这个过程，直到把所有的书都放在书架上。

需要注意的是，在上述过程的每个步骤中，摆放书的顺序与你整理好的顺序相同。 例如，如果这里有 5 本书，那么可能的一种摆放情况是：第一和第二本书放在第一层书架上，第三本书放在第二层书架上，第四和第五本书放在最后一层书架上。

每一层所摆放的书的最大高度就是这一层书架的层高，书架整体的高度为各层高之和。

以这种方式布置书架，返回书架整体可能的最小高度。

 

 
**示例**
> 输入：books = [[1,1],[2,3],[2,3],[1,1],[1,1],[1,1],[1,2]], shelf_width = 4
输出：6
解释：
3 层书架的高度和为 1 + 3 + 2 = 6 。
第 2 本书不必放在第一层书架上。

 
#### 解题思路
***
 本题简单的一点就在于摆放的顺序和原顺序一致

定义dp[i]为前i本书能够到达的最小高度。
则对于第i+1本书，有两类选择。
如自己单独一层，则状态转移方程为dp[i+1] = dp[i] + h[i+1]
如果和前面的书放在一起，则状态转移方程为
dp[i+1] = min(dp[j] + max[h[j+1] ~ h[i+1])),
 其中需要满足sum(w[j+1] ~ w[i+1]) <= shelf_width，含义是前j本书组成若干层，第j+1到第i+1本书组成一层。
对于这些选择，取最小值


#### 代码实现
```python
class Solution(object):
    def minHeightShelves(self, books, shelf_width):
        """
        :type books: List[List[int]]
        :type shelf_width: int
        :rtype: int
        """
        n = len(books)
        dp = [1000000] * (n+1)
        dp[0] = 0
        
        for i in range(1, n+1):
            w, j, h = 0, i, 0
            while j>0:
                w += books[j-1][0]
                if w>shelf_width:
                    break
                h = max(h, books[j-1][1])
                dp[i] = min(dp[i], dp[j-1]+h)
                j -= 1
        return dp[-1]
```

本文链接：[https://www.jianshu.com/p/cf4c0054db09](https://www.jianshu.com/p/cf4c0054db09)
