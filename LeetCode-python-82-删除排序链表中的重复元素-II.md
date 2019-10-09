 [题目链接](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list-ii/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：链表
***
给定一个排序链表，删除所有含有重复数字的节点，只保留原始链表中 没有重复出现 的数字。

**示例1**
>输入: 1->2->3->3->4->4->5
输出: 1->2->5

**示例2**
>输入: 1->1->1->2->3
输出: 2->3

#### 解题思路
***
**In-place的算法**
新建一个pre节点，pre节点的下一个节点分两种情况：
1.如果遇到重复的元素,如示例1中，head.val==head.next.val==3，pre.next就指向重复元素之后第一个不等于3的节点，即跨过了重复的元素，指向第一个4
2.如果遇到不重复的元素，pre就更新为pre.next，因为pre指向的链表就是原链表，所以pre.next是有值的

 
#### 代码实现
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def deleteDuplicates(self, head: ListNode) -> ListNode:
        dummy = pre = ListNode(0)
        dummy.next = head
        while head and head.next:
            if head.val == head.next.val:
                # 比较过的就跳过
                head = head.next
                while head.next and head.val == head.next.val:
                    head = head.next
                    print(head.val)
                pre.next = head.next
            else:
                pre = pre.next
            head = head.next        
        return dummy.next
```

本文链接：[https://www.jianshu.com/p/31dbf029a0cc](https://www.jianshu.com/p/31dbf029a0cc)
