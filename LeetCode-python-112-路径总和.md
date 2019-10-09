 [题目链接](https://leetcode-cn.com/problems/path-sum/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树、深度优先搜索、递归
***
 给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。

说明: 叶子节点是指没有子节点的节点。

**示例**
给定如下二叉树，以及目标和 sum = 22
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
```
#### 解题思路
***
 深度优先搜索，只有在搜索到叶子节点时判断是否总和等于目标，只要有一条路径总和等于目标，就返回true

如果不是叶子节点，就对该节点的孩子节点分别进行深度优先搜索

#### 代码实现
深度优先搜索
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def hasPathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: bool
        """
        res = []
        def dfs(target, root):
            if not root.left and not root.right:
                if root.val == target:
                    res.append(True)
            if root.left:
                dfs(target-root.val, root.left)
            if root.right:
                dfs(target-root.val, root.right)
        if not root:
            return False
        dfs(sum, root)
        return any(res)
```
递归：
```python
class Solution(object):
    def hasPathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: bool
        """
        if not root:
            return False
        if not root.left and not root.right and sum = root.val:
            return True
        sum -= root.val
        return self.hasPathSum(root.left, sum) or self.hasPathSum(root.right, sum)
```
本文链接：[https://www.jianshu.com/p/6f15488d42aa](https://www.jianshu.com/p/6f15488d42aa)

 
