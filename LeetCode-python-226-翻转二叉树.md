 [题目链接](https://leetcode-cn.com/problems/invert-binary-tree/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树
***
 翻转一棵二叉树。

 
 
#### 解题思路
***
 从底下往上依次翻转



#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def invertTree(self, root):
        """
        :type root: TreeNode
        :rtype: TreeNode
        """
        if root:               
            root.left, root.right = self.invertTree(root.right), self.invertTree(root.left)
        return root
            
```

本文链接：[https://www.jianshu.com/p/adb0ac694e9b](https://www.jianshu.com/p/adb0ac694e9b)
