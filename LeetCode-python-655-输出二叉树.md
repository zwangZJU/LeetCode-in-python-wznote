 [题目链接](https://leetcode-cn.com/problems/print-binary-tree/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 二叉树 
***
 在一个 m*n 的二维字符串数组中输出二叉树，并遵守以下规则：

- 行数 m 应当等于给定二叉树的高度。
- 列数 n 应当总是奇数。
- 根节点的值（以字符串格式给出）应当放在可放置的第一行正中间。根节点所在的行与列会将剩余空间划分为两部分（左下部分和右下部分）。你应该将左子树输出在左下部分，右子树输出在右下部分。左下和右下部分应当有相同的大小。即使一个子树为空而另一个非空，你不需要为空的子树输出任何东西，但仍需要为另一个子树留出足够的空间。然而，如果两个子树都为空则不需要为它们留出任何空间。
- 每个未使用的空间应包含一个空的字符串""。
- 使用相同的规则输出子树。


 
**示例1**
> 输入:
     1
    /
   2
输出:
[["", "1", ""],
 ["2", "", ""]]

**示例2**
>输入:
     1
    / \
   2   3
    \
     4
输出:
[["", "", "", "1", "", "", ""],
 ["", "2", "", "", "", "3", ""],
 ["", "", "4", "", "", "", ""]]

#### 解题思路
***
 1.计算输出矩阵的行数和列数
行数row是二叉树的最大高度height
列数col是$2^{height}-1$，即矩阵宽度width

2.计算每个节点所在的位置
根节点在第0行的第mid列,其中mid=(0+width-1)/2
根节点的左节点在第1行的第(0+mid-1)/2列，右节点在第1行的第(mid+1+widht-1)列
归纳一下，若第i行的节点的位置是mid =(left+right)/2，该节点的左节点的位置是[left, mid]的中间点，该节点的右节点的位置是[mid,right]的中间点

3.遍历二叉树

#### 代码实现
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def printTree(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[str]]
        """
        def get_height(node):
            return 1+max(get_height(node.left), get_height(node.right)) if node else 0
        
        def get_output(node, row, left, right):
            if not node:
                return 
            mid = (left + right) // 2
            self.output[row][mid] = str(node.val)
            get_output(node.left, row+1, left, mid-1)
            get_output(node.right, row+1, mid+1, right)
            
        height = get_height(root)
        width = 2 ** height - 1
        self.output = [[""] * width for _ in range(height)]
        get_output(root, 0, 0, width-1)
        return self.output
        
```

本文链接：[https://www.jianshu.com/p/ed55eefe506f](https://www.jianshu.com/p/ed55eefe506f)
