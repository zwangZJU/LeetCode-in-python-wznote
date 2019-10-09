 [题目链接](https://leetcode-cn.com/problems/rotate-list/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：链表
***
给定一个链表，旋转链表，将链表每个节点向右移动 k 个位置，其中 k 是非负数。

**示例1**
>输入: 1->2->3->4->5->NULL, k = 2
输出: 4->5->1->2->3->NULL
解释:
向右旋转 1 步: 5->1->2->3->4->NULL
向右旋转 2 步: 4->5->1->2->3->NULL

**示例2**
>输入: 0->1->2->NULL, k = 4
输出: 2->0->1->NULL
解释:
向右旋转 1 步: 2->0->1->NULL
向右旋转 2 步: 1->2->0->NULL
向右旋转 3 步: 0->1->2->NULL
向右旋转 4 步: 2->0->1->NULL
#### 解题思路
***
1.用快慢指针确定旋转后链表的头节点
若链表的长度为n，让快指针先走k%n步，然后快慢指针同时向前走，直到快指针的next为空，此时慢指针的next为旋转后链表的头节点
2.移花接木
快指针的next指向原链表的头节点head
head指向慢指针的next，作为新链表的头节点返回
断掉慢指针和head之间的链，否则会形成环

#### 代码实现
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def rotateRight(self, head: ListNode, k: int) -> ListNode:
        if not head or not head.next:
            return head
        
        fast, slow = head, head
        # 找到fast的起始节点
        def findStart(fast, k):
            length = 0
            while k>0:
                k -= 1
                length += 1
                fast = fast.next
                if not fast:
                    fast = head                                    
                    k = k % length                    
                    return findStart(fast, k)
            return fast
                   
        fast = findStart(fast, k)
         
        while fast and fast.next:           
            fast = fast.next
            slow = slow.next
   
        fast.next = head
        head = slow.next
        slow.next = None
        return head
```
