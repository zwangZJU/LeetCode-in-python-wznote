 [题目链接](https://leetcode-cn.com/problems/binary-tree-level-order-traversal-ii/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树
***
 给定一个二叉树，返回其节点值自底向上的层次遍历。 （即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历）

 
**示例**
给定二叉树 [3,9,20,null,null,15,7]
```
    3
   / \
  9  20
    /  \
   15   7
```
返回其自底向上的层次遍历为：
```
[
  [15,7],
  [9,20],
  [3]
]
```

#### 解题思路
***
层序遍历，每遍历一层，把结果放在上一层的前面



#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def levelOrderBottom(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if not root:
            return []
        queue = [root]
        res = [[root.val]]
        while queue:
            LR_pair = [(node.left, node.right) for node in queue]
            queue = [node for LR in LR_pair for node in LR if node]
            if queue:
                res = [[node.val for node in queue]] + res
        return res
```
本文链接：[https://www.jianshu.com/p/29f717bbcce4](https://www.jianshu.com/p/29f717bbcce4)

 
