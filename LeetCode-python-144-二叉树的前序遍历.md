 [题目链接](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/)
难度：困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树
***
给定一个二叉树，返回它的 前序 遍历。

 
**示例**
```
输入: [1,null,2,3]  
   1
    \
     2
    /
   3 

输出: [1,2,3]
```

#### 解题思路
***
1. 初始化一个栈，里面存储着根节点
2. 取出栈顶节点，将改节点的值存储在遍历的结果中，将其右孩子和左孩子依次入栈
3. 重复第2步，直到栈为空

因为栈是先进后出，所以右孩子先进栈，左孩子后进栈，出栈的时候就会先出左孩子，保证了遍历的顺序

#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        if not root:
            return []
        stack = [root]
        output = []
        while stack:
            node = stack.pop()
            if not node:
                continue
            output.append(node.val)
            stack.append(node.right)
            stack.append(node.left)
        return output
        
```
本文链接：[https://www.jianshu.com/p/04fdaa7f15fe](https://www.jianshu.com/p/04fdaa7f15fe)

 
