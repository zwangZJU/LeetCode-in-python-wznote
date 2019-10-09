 [题目链接](https://leetcode-cn.com/problems/binary-tree-right-side-view/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树
***
 给定一棵二叉树，想象自己站在它的右侧，按照从顶部到底部的顺序，返回从右侧所能看到的节点值。

 
**示例**
> 输入: [1,2,3,null,5,null,4]
输出: [1, 3, 4]

#### 解题思路
***
 层序遍历，输出每层的最后一个
![](https://upload-images.jianshu.io/upload_images/15048949-e3b4f7207bf5aa16.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
图片来源[https://leetcode-cn.com/problems/binary-tree-right-side-view/solution/er-cha-shu-de-you-shi-tu-by-leetcode/](https://leetcode-cn.com/problems/binary-tree-right-side-view/solution/er-cha-shu-de-you-shi-tu-by-leetcode/)


#### 代码实现
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def rightSideView(self, root: TreeNode) -> List[int]:
        view = []
        if root:
            level = [root]
            while level:
                view.append(level[-1].val)
                level = [kid for node in level for kid in (node.left, node.right) if kid]
        return view
```

本文链接：[https://www.jianshu.com/p/f32b669a4dd4](https://www.jianshu.com/p/f32b669a4dd4)
