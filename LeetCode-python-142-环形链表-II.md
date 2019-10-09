[题目链接](https://leetcode-cn.com/problems/linked-list-cycle-ii/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：链表
***
给定一个链表，返回链表开始入环的第一个节点。 如果链表无环，则返回 null。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。

说明：不允许修改给定的链表。
 

#### 解题思路
***
1.判断是否有环（快慢指针）
开始时，快慢指针都指向头节点，快指针fast每次走2步，慢指针slow每次走1步，如果快指针和慢指针在某一步指向同一个节点，说明有环
2.判断入环的第一个节点
性质：当快指针和慢指针相遇时，若慢指针此时走了k步，则快指针走了2k步，慢指针从当前节点走k步后会回到当前节点（因为有环）
在快慢指针相遇时，将快指针放到链表头部，每次走一步，慢指针在相遇的节点开始，每次走一步，当两个指针再次指向同一个节点时，该节点为链表的入口节点

#### 代码实现
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def detectCycle(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head or not head.next  or not head.next.next:
            return None        
        fast = head 
        slow = head 
        while fast and slow:
            try:
                fast = fast.next.next
            except:
                return None
            slow = slow.next   
            if fast == slow:
                fast = head
                while True: 
                    if fast == slow:
                        return slow
                    fast = fast.next
                    slow = slow.next                        
        return None
```

本文链接：[https://www.jianshu.com/p/b9e67aae6d7e](https://www.jianshu.com/p/b9e67aae6d7e)
