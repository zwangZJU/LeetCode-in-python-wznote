 [题目链接](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树，递归
***
 给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

 
**示例**
给定二叉树 [3,9,20,null,null,15,7]
```
    3
   / \
  9  20
    /  \
   15   7
```

#### 解题思路
***
 最大的深度是左子树或右子树中深度中更大的一个+1，递归的在子树的子树中寻找



#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root:
            return 0
        left = self.maxDepth(root.left)
        right = self.maxDepth(root.right)
        return max(left, right) + 1
```
本文链接：[https://www.jianshu.com/p/f6becaba832d](https://www.jianshu.com/p/f6becaba832d)

 
