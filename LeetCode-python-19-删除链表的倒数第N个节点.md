 [题目链接](https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
 给定一个链表，删除链表的倒数第 n 个节点，并且返回链表的头结点。

 
**示例**
> 给定一个链表: 1->2->3->4->5, 和 n = 2.
当删除了倒数第二个节点后，链表变为 1->2->3->5.

#### 解题思路
***
 为了删除倒数第n个节点，需要找到倒数第n+1个节点，让倒数第n+1个节点的next指向倒数第n个节点的下一个节点
用快慢指针定位倒数第n+1个节点：
初始时让fast和slow同时指向head,让fast指针先走n+1步，然后fast和slow同时往前走，指导fast指向空节点（链表尾），此时slow正好指向倒数第n+1个节点，删除第n个节点后返回head即可

注意一种特殊情况，即倒数第n个节点是头结点的时候，即fast走了n步就指向空节点了，此时 直接返回head.next即可



#### 代码实现
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def removeNthFromEnd(self, head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        fast = slow = head
        while n>0:
            fast = fast.next
            n -= 1
        if not fast:
            return head.next
        else:
            fast = fast.next
        while fast:
            fast = fast.next
            slow = slow.next
        slow.next = slow.next.next
        return head
        
```

本文链接：[https://www.jianshu.com/p/797102f06aae](https://www.jianshu.com/p/797102f06aae)
