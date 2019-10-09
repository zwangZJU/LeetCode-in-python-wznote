 [题目链接](https://leetcode-cn.com/problems/insertion-sort-list/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：链表、排序  
***
对链表进行插入排序。
 ![](https://upload-images.jianshu.io/upload_images/15048949-d7c09e575e546dbb.gif?imageMogr2/auto-orient/strip)


 
**示例1**
> 输入: 4->2->1->3
输出: 1->2->3->4

**示例2**
>输入: -1->5->3->4->0
输出: -1->0->3->4->5
#### 解题思路
***
 链表不能倒着遍历，所以每次在插入之前作比较时，都是从头开始比较的，若当前节点的值大于前一个结点的值，则不用进行比较和插入，当前指针直接指向后一位即可



#### 代码实现
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def insertionSortList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head:
            return head
        dummy = ListNode(0)
        dummy.next = head
        pre, cur = head, head.next

        while cur:        
            if cur.val>pre.val:
                pre, cur= cur, cur.next
                continue
            pre.next = cur.next
            h = dummy            
            while h.next.val<cur.val:                
                h = h.next           
            t = h.next
            h.next = cur           
            cur.next = t
            cur = pre.next
            
        return dummy.next
            
```

本文链接：[https://www.jianshu.com/p/b1e56e2af390](https://www.jianshu.com/p/b1e56e2af390)
