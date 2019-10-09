 [题目链接](https://leetcode-cn.com/problems/same-tree/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  树、递归
***
给定两个二叉树，编写一个函数来检验它们是否相同。

如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。 

 
**示例1**
```
输入:       1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]
输出: true
```
**示例2**
```
输入:      1          1
          /           \
         2             2

        [1,2],     [1,null,2]
输出: false
```

#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: TreeNode
        :type q: TreeNode
        :rtype: bool
        """
        if p and q:
            return p.val == q.val and self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
        else:
            return p is q
```

本文链接： [https://www.jianshu.com/p/48c8b05c8fa1](https://www.jianshu.com/p/48c8b05c8fa1)
