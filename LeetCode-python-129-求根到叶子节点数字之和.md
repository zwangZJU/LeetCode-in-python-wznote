 [题目链接](https://leetcode-cn.com/problems/sum-root-to-leaf-numbers/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 
给定一个二叉树，它的每个结点都存放一个 0-9 的数字，每条从根到叶子节点的路径都代表一个数字。

例如，从根到叶子节点路径 1->2->3 代表数字 123。

计算从根到叶子节点生成的所有数字之和。

说明: 叶子节点是指没有子节点的节点。
 
 
**示例1**
> 输入: [1,2,3]
    1
   / \
  2   3
输出: 25
解释:
从根到叶子节点路径 1->2 代表数字 12.
从根到叶子节点路径 1->3 代表数字 13.
因此，数字总和 = 12 + 13 = 25.
 

**示例2**
>输入: [4,9,0,5,1]
    4
   / \
  9   0
 / \
5   1
输出: 1026
解释:
从根到叶子节点路径 4->9->5 代表数字 495.
从根到叶子节点路径 4->9->1 代表数字 491.
从根到叶子节点路径 4->0 代表数字 40.
因此，数字总和 = 495 + 491 + 40 = 1026.
 
#### 解题思路
***
 从上到下遍历二叉树，逐节点进行num*10+root.val计算



#### 代码实现
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def sumNumbers(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        
        if not root:
            return 0
       
        self.res = 0
        def calc(root, num):
             
            if not root.left and not root.right:
                
                self.res += num*10+root.val
            if root.left:                
                calc(root.left, num*10+root.val)
            if root.right:
                calc(root.right, num*10+root.val)    
        calc(root, 0)
       
        return self.res
```

本文链接：[https://www.jianshu.com/p/1b2da2b54f7c](https://www.jianshu.com/p/1b2da2b54f7c)
