 [题目链接](https://leetcode-cn.com/problems/binary-tree-zigzag-level-order-traversal/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：栈  
***
 给定一个二叉树，返回其节点值的锯齿形层次遍历。（即先从左往右，再从右往左进行下一层遍历，以此类推，层与层之间交替进行）。

例如：
 给定二叉树 [3,9,20,null,null,15,7],
返回：[
  [3],
  [20,9],
  [15,7]
]
#### 解题思路
***
 二叉树的层序遍历，奇数行需要翻转



#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def zigzagLevelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root:
            return []
        stack = [root]
        res = []
        flag = 1
        while stack:
            t = [node.val for node in stack]
            res.append(t[::flag])
            flag *= -1
            stack = [ kid for node in stack for kid in (node.left, node.right) if kid]
        return res
```

本文链接：[https://www.jianshu.com/p/53cb9757fc85](https://www.jianshu.com/p/53cb9757fc85)
