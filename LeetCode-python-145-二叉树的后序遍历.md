 [题目链接](https://leetcode-cn.com/problems/binary-tree-postorder-traversal/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树
***
 给定一个二叉树，返回它的 后序 遍历。

 
**示例**
```
输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [3,2,1]
```
#### 解题思路
***
递归好实现一点，不递归确实很麻烦，毕竟是一道困难等级的题目

对于非递归的方法，有一种思路，用先序遍历（中->左->右）的方式，以中->右->左的顺序遍历二叉树，最后再翻转结果就可以得到后续遍历


#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def postorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res = []
        def post(cur):
            if cur:
                post(cur.left)
                post(cur.right)
                res.append(cur.val)
        post(root)
        return res
```
本文链接：[https://www.jianshu.com/p/b83dd7571416](https://www.jianshu.com/p/b83dd7571416)

 
