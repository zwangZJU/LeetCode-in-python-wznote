 [题目链接](https://leetcode-cn.com/problems/binary-tree-paths/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树、深度优先搜索
***
给定一个二叉树，返回所有从根节点到叶子节点的路径。

说明: 叶子节点是指没有子节点的节点。 

 
**示例**
```
输入:

   1
 /   \
2     3
 \
  5

输出: ["1->2->5", "1->3"]
```

#### 解题思路
***
 深度优先搜索：
先往左子树搜，再往右子树搜，记录访问过的节点
停止的条件是到了叶子节点，即该节点没有孩子节点了。



#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def binaryTreePaths(self, root):
        """
        :type root: TreeNode
        :rtype: List[str]
        """
        res = []
        def dfs(root, path):
            if not root.left and not root.right:
                res.append('->'.join(path+[str(root.val)]))
            if root.left:
                dfs(root.left, path+[str(root.val)])
            if root.right:
                dfs(root.right, path+[str(root.val)])
        if not root:
            return []
        dfs(root, [])
        return res
```

本文链接：
