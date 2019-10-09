 [题目链接](https://leetcode-cn.com/problems/word-search/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组、字符串、深度优先搜索
***
 给定一个二维网格和一个单词，找出该单词是否存在于网格中。

单词必须按照字母顺序，通过相邻的单元格内的字母构成，其中“相邻”单元格是那些水平相邻或垂直相邻的单元格。同一个单元格内的字母不允许被重复使用。
 
 
**示例**
> board =
[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]
给定 word = "ABCCED", 返回 true.
给定 word = "SEE", 返回 true.
给定 word = "ABCB", 返回 false.


#### 解题思路
***
深度优先搜索
注意：搜索过的地方需要有标记，以免重复搜索



#### 代码实现
```python
class Solution(object):
    def exist(self, board, word):
        """
        :type board: List[List[str]]
        :type word: str
        :rtype: bool
        """
        n, m = len(board), len(board[0])
        
        def dfs(board, x, y, word):
            if not word:
                return True
            if 0<=x<n and 0<=y<m and board[x][y] == word[0] and board[x][y]!='#':
                
                t, board[x][y] = board[x][y], '#'    
                res =  dfs(board, x, y+1, word[1:]) or dfs(board, x, y-1, word[1:]) or dfs(board, x+1, y, word[1:]) or dfs(board, x-1, y, word[1:])
                board[x][y] = t
                return res
                         
            return False
        for i in range(n):
            for j in range(m):
                if dfs(board,i,j,word):
                    return True
        return False
```

本文链接：[https://www.jianshu.com/p/a3467aaf5633](https://www.jianshu.com/p/a3467aaf5633)
