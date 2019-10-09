[题目链接](https://leetcode-cn.com/problems/odd-even-linked-list/)

难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
给定一个单链表，把所有的奇数节点和偶数节点分别排在一起。请注意，这里的奇数节点和偶数节点指的是节点编号的奇偶性，而不是节点的值的奇偶性。

请尝试使用原地算法完成。你的算法的空间复杂度应为 O(1)，时间复杂度应为 O(nodes)，nodes 为节点总数。 

 
**示例1**
> 输入: 1->2->3->4->5->NULL
输出: 1->3->5->2->4->NULL

**示例2**
>输入: 2->1->3->5->6->4->7->NULL 
输出: 2->3->6->7->1->5->4->NULL

#### 解题思路
***
 第0个节点为偶头节点，第1个节点为奇头节点
两个头节点开始往下连，当前节点的下一个节点应该为当前节点的下下个节点，即跳过一个节点
遍历到最后一个节点后，
偶尾节点连接奇头节点



#### 代码实现
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def oddEvenList(self, head: ListNode) -> ListNode:
        if not head or not head.next:
            return head        
        odd_head = odd = head.next       
        even = head
        while even and even.next and odd and odd.next:
            even.next = even.next.next
            even = even.next
            odd.next = odd.next.next
            odd = odd.next
            
        even.next = odd_head
        
        return head
```

本文链接：[https://www.jianshu.com/p/543a966704f2](https://www.jianshu.com/p/543a966704f2)
