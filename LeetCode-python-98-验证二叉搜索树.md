 [题目链接](https://leetcode-cn.com/problems/validate-binary-search-tree/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树
***
给定一个二叉树，判断其是否是一个有效的二叉搜索树。

假设一个二叉搜索树具有如下特征：

节点的左子树只包含小于当前节点的数。
节点的右子树只包含大于当前节点的数。
所有左子树和右子树自身必须也是二叉搜索树。
 
**示例**
```
输入:
    2
   / \
  1   3
输出: true
```

**示例**
```
输入:
    5
   / \
  1   4
     / \
    3   6
输出: false
解释: 输入为: [5,1,4,null,null,3,6]。
     根节点的值为 5 ，但是其右子节点值为 4 。

```
#### 解题思路
***
 对于每一个节点：
1. 其左孩子的值一定小于它，右孩子一定大于它
这还不够
2. 必须左子树的所有节点的值都小于它，右孩子的所有节点的值都大于它

例如：
```
输入:
    5
   / \
  1   7
     / \
    6   8
```
满足条件1，但不满足条件2，因为6大于5了
所以，得给左子树找一个上界，右子树找一个下界，均为当前节点，而左子树的下界和右子树的上界沿用当前节点的上下界

#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isValidBST(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
         
        def judge(root, lower, upper):
            if not root:
                return True
            if lower < root.val  < upper:
               return judge(root.left, lower, root.val) and judge(root.right, root.val, upper)
            return False
        return judge(root, -float('INF'), float('INF'))
```
本文链接：[https://www.jianshu.com/p/198a20feab2e](https://www.jianshu.com/p/198a20feab2e)

 
