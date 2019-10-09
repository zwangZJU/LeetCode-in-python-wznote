 [题目链接](https://leetcode-cn.com/problems/partition-list/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：链表
***
给定一个链表和一个特定值 x，对链表进行分隔，使得所有小于 x 的节点都在大于或等于 x 的节点之前。

你应当保留两个分区中每个节点的初始相对位置。

**示例**
>输入: head = 1->4->3->2->5->2, x = 3
输出: 1->2->2->4->3->5

#### 解题思路
***
新建两个链表left和right，遍历原链表，值小于x的节点接在left后，值大于等于x的节点接在right后
再将left和right相接
返回left的头节点

注意：
为了能连接两个链表以及返回新链表，需要在初始化的时候保存两个链表的头节点

#### 代码实现
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def partition(self, head: ListNode, x: int) -> ListNode:
        left_head = left = ListNode(0)   
        right_head = right = ListNode(0)
        while head:
            val = head.val
            if val < x:
                left.next = head
                left = left.next
            else:
                right.next = head
                right = right.next
            head = head.next
        right.next = None
        left.next = right_head.next 
        return left_head.next
```

本文链接：[https://www.jianshu.com/p/5870049789a0](https://www.jianshu.com/p/5870049789a0)
