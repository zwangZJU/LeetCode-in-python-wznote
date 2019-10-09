 [题目链接](https://leetcode-cn.com/problems/maximal-square/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
 给定一个单链表 L：L0→L1→…→Ln-1→Ln ，
将其重新排列后变为： L0→Ln→L1→Ln-1→L2→Ln-2→…

你不能只是单纯的改变节点内部的值，而是需要实际的进行节点交换。

 
**示例1**
> 给定链表 1->2->3->4, 重新排列为 1->4->2->3.

**示例2**
>给定链表 1->2->3->4->5, 重新排列为 1->5->2->4->3.

#### 解题思路
***
先找到链表的中点：快慢指针，考虑节点个数奇偶情况
再翻转后半段链表
最后两链表依次插入



#### 代码实现
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reorderList(self, head):
        """
        :type head: ListNode
        :rtype: None Do not return anything, modify head in-place instead.
        """
        # looking for the midpoint
        fast = slow = a = head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next    
        b = slow.next if fast else slow
        
        # reverse
        pre = None
        cur = b
        while cur:
            next = cur.next
            cur.next = pre
            pre = cur
            cur = next
            
        # cross
        b = pre
        while a:
            a.next, b = b, a.next
            a = a.next
        return head
```

本文链接：[https://www.jianshu.com/p/0025ef59ee07](https://www.jianshu.com/p/0025ef59ee07)
