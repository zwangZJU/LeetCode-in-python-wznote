 [题目链接](https://leetcode-cn.com/problems/swap-nodes-in-pairs/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
 给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。

你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

 
**示例**
> 给定 1->2->3->4, 你应该返回 2->1->4->3.
#### 解题思路
***
 两个节点交换：
1. 先保存head.next.next的节点为new_start，不然换完就找不到了
2. 两节点交换：head, head.next = head.next, head
3. 续上之后的链表，head.next.next = new_start
4.以new_start开始重复1-3步，知道链表结尾，返回head

为了简化代码，可以用递归，修改第3步为：
head.next.next = self.swapPairs(new_start)


#### 代码实现
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def swapPairs(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next: return head
        new_start = head.next.next
        head, head.next = head.next, head
        head.next.next = self.swapPairs(new_start)
        return head
```

本文链接：[https://www.jianshu.com/p/bc283e46001f](https://www.jianshu.com/p/bc283e46001f)
