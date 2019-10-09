 [题目链接](https://leetcode-cn.com/problems/delete-node-in-a-linked-list/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
 请编写一个函数，使其可以删除某个链表中给定的（非末尾）节点，你将只被给定要求被删除的节点。

 
**示例1**
> 输入: head = [4,5,1,9], node = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9.

**示例2**
>输入: head = [4,5,1,9], node = 1
输出: [4,5,9]
解释: 给定你链表中值为 1 的第三个节点，那么在调用了你的函数之后，该链表应变为 4 -> 5 -> 9.

#### 解题思路
***
删除节点的方法就是让该节点上一节点的next直接指向该节点的下一个节点，跨过该节点
 但由于只告诉了当前要删除的节点，根据链表的性质可知，无法获得该节点的前一个节点
所以，让要删除的节点的val等于该节点下一个节点的val，再删除下一个节点即可



#### 代码实现
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val = node.next.val
        node.next = node.next.next
```

本文链接：[https://www.jianshu.com/p/50c139048677](https://www.jianshu.com/p/50c139048677)
