 [题目链接](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树
***
给定一个二叉树，返回其按层次遍历的节点值。 （即逐层地，从左到右访问所有节点）。

 
**示例**
 给定二叉树: [3,9,20,null,null,15,7]
```
    3
   / \
  9  20
    /  \
   15   7
```
返回其层次遍历结果：
```
[
  [3],
  [9,20],
  [15,7]
]
```

#### 解题思路
***
方法1：广度优先搜索
每一层的所有节点从左往右顺序存在队列里，下一层的所有节点就是当前队列按顺序出队的左右孩子组成的队列，当然，要去掉为空的子节点

方法2：深度优先搜索
先左子树后右子树，搜索的时候保存搜索的深度值，深度值相同的节点放在一起



#### 代码实现
方法1：
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        if not root:
            return []
        res, level = [], [root]
        while level:
            res.append([node.val for node in level])
            LR_pair = [(node.left, node.right) for node in level]
            level = [leaf for LR in LR_pair for leaf in LR if leaf]   
        return res
```

方法2：
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        res = []
        def dfs(root, level):
            if root:
                if len(res)<level+1:
                    res.append([])
                res[level].append(root.val)
                dfs(root.left, level+1)
                dfs(root.right, level+1)
        dfs(root, 0)
        return res
```

本文链接：[https://www.jianshu.com/p/74b17cb8d0bd](https://www.jianshu.com/p/74b17cb8d0bd)

 
