 [题目链接](https://leetcode-cn.com/problems/sum-of-left-leaves/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树
***
 计算给定二叉树的所有左叶子之和。

 
 
#### 解题思路
***
 递归
如果一个节点的左孩子没有孩子，就是左叶子



#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def sumOfLeftLeaves(self, root: TreeNode) -> int:
        if not root:
            return 0
        
        if root.left and not root.left.left and not root.left.right:
            return root.left.val + self.sumOfLeftLeaves(root.right)
        return self.sumOfLeftLeaves(root.left) + self.sumOfLeftLeaves(root.right)
```

本文链接：[https://www.jianshu.com/p/cf9ce34af64c](https://www.jianshu.com/p/cf9ce34af64c)
