 [题目链接](https://leetcode-cn.com/problems/minimum-path-sum/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  
***
 在 O(n log n) 时间复杂度和常数级空间复杂度下，对链表进行排序。

 
**示例1**
> 输入: 4->2->1->3
输出: 1->2->3->4

**示例2**
> 输入: -1->5->3->4->0
输出: -1->0->3->4->5

#### 解题思路
***
 归并排序
1. 用快慢指针把链表分成两部分，对每一部分重复这一操作，直到某一部分只存在一个节点，返回这个节点，对于一个节点来说，它一定是有序的
2. 对两个有序链表进行融合，合成一个链表



#### 代码实现
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None
 
class Solution(object):

    def sortList(self, head):
        if not head or not head.next:
            return head
        # 分成两半
        fast, slow = head.next, head
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
        second = slow.next

        slow.next = None
        l = self.sortList(head)
        r = self.sortList(second)
        return self.merge(l, r)

     
    def merge(self, l, r):
        if not l or not r:
            return l or r
        if l.val > r.val:
            l, r = r, l
        # 保存头节点用于返回
        head = pre = l
        l = l.next
        while l and r:
            if l.val < r.val:
                l = l.next
            else:
                nxt = pre.next
                pre.next = r
                tmp = r.next
                r.next = nxt
                r = tmp
            pre = pre.next

        pre.next = l or r
        return head
```
本文链接：[https://www.jianshu.com/p/fa17c59ebab0](https://www.jianshu.com/p/fa17c59ebab0)

 
