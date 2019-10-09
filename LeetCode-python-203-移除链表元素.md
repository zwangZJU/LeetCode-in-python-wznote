 [题目链接](https://leetcode-cn.com/problems/remove-linked-list-elements/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
 删除链表中等于给定值 val 的所有节点。

 
**示例**
> 输入: 1->2->6->3->4->5->6, val = 6
输出: 1->2->3->4->5

#### 解题思路
***
 遍历链表，断掉所有节点值等于val的链
cur表示当前的节点，pre代表cur的前一个节点
当cur.val == val时，pre.next = cur.next，这样，就跨过了这个节点，此时，cur也要指向cur.next
当cur.val != val时，此时不用删除，则pre=pre.next，cur=cur.next

注意：
并不是每一步都更新pre的，因为pre指向的节点的值必须时不等于val，当删除一个节点时，并不知道下一个节点是否也等于val，所以不能更新pre

特殊情况：
要考虑第一个节点要被删除的情况



#### 代码实现
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def removeElements(self, head: ListNode, val: int) -> ListNode:
        pre = ListNode(0)
        dummy = pre
        pre.next = head
        cur = head
        while cur:
            if cur.val == val:
                pre.next = cur.next                
            else:
                pre = pre.next
            cur = cur.next
        return dummy.next
```

本文链接：[https://www.jianshu.com/p/46c9c84310bd](https://www.jianshu.com/p/46c9c84310bd)
