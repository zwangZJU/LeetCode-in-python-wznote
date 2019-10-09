 [题目链接](https://leetcode-cn.com/problems/merge-two-sorted-lists/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
 将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

 
**示例**
> 输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4

#### 解题思路
***
 初始化一个头节点cur
两个链表各有一个指针指向各自头节点，谁小就接在cur后面，相应的指针后移一位，直到有一个链表遍历到尾，把另一个链表的剩下部分接在cur后



#### 代码实现
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        dummy = cur = ListNode(0)
        while l1 and l2:
            if l1.val < l2.val:
                cur.next = l1
                l1 = l1.next
            else:
                cur.next = l2
                l2 = l2.next
            cur = cur.next
        cur.next = l1 or l2
        return dummy.next
```

本文链接：[https://www.jianshu.com/p/d37f1b1a11fe](https://www.jianshu.com/p/d37f1b1a11fe)
