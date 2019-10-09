 [题目链接](https://leetcode-cn.com/problems/path-sum-ii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树、深度优先搜索
***
给定一个二叉树和一个目标和，找到所有从根节点到叶子节点路径总和等于给定目标和的路径。

说明: 叶子节点是指没有子节点的节点。

 
**示例**
给定如下二叉树，以及目标和 sum = 22
```
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \    / \
        7    2  5   1
```
返回：
```
[
   [5,4,11,2],
   [5,8,4,5]
]
```
#### 解题思路
***
 和112题一样，在搜索的时候保存下路径即可



#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def pathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: List[List[int]]
        """
        res = []
        def dfs(target, root, path):
            if not root.left and not root.right:
                if target == root.val:
                    res.append(path+[root.val])
            if root.left:
                dfs(target-root.val, root.left, path+[root.val])
            if root.right:
                dfs(target-root.val, root.right, path+[root.val])
        if not root:
            return []
        dfs(sum, root, [])
        return res
```
本文链接：[https://www.jianshu.com/p/d6dd05f7c6c4](https://www.jianshu.com/p/d6dd05f7c6c4)

 
