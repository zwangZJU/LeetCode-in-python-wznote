 [题目链接](https://leetcode-cn.com/problems/unique-binary-search-trees-ii/)
难度：中等         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  二叉树、递归
***
 给定一个整数 n，生成所有由 1 ... n 为节点所组成的二叉搜索树。

 
**示例**
> 输入: 3
输出:
[
  [1,null,3,2],
  [3,2,null,1],
  [3,1,null,null,2],
  [2,1,3],
  [1,null,2,null,3]
]

#### 解题思路
***
 以每一个i都作一次根节点，i将数列分为两部分，（1，i-1）和（i+1, n)，在前一个区间中让每个j都做一次根节点构成的树作为i的左子树，在后一个区间中让每个k都做一次根节点构成的树作为i的右子树，将所有的情况组合起来

来回只用到一个函数用来生成以i为根节点的树，递归调用即可，结束的条件就是没有节点可以生成，返回[None]



#### 代码实现
```python
class Solution(object):
    def generateTrees(self, n):
        """
        :type n: int
        :rtype: List[TreeNode]
        """
        if n == 0:
            return []
        def generate(start, end):
            trees = []
            for root in range(start, end):
                for left in generate(start, root):
                    for right in generate(root+1, end):
                        node = TreeNode(root)
                        node.left = left
                        node.right = right
                        trees.append(node)
              
            return trees or [None]
        return generate(1,n+1)
```

本文链接：[https://www.jianshu.com/p/b21dc2b1e5f7](https://www.jianshu.com/p/b21dc2b1e5f7)
