 [题目链接](https://leetcode-cn.com/problems/reverse-linked-list-ii/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 链表
***
 反转从位置 m 到 n 的链表。请使用一趟扫描完成反转。

说明:
1 ≤ m ≤ n ≤ 链表长度。

 
**示例**
>输入: 1->2->3->4->5->NULL, m = 2, n = 4
输出: 1->4->3->2->5->NULL

#### 解题思路
***
0.保存头节点
1.找到反转部分的前一个节点，保存为start
2.翻转第m到n位链表，记录第m个节点为node_m，第n个节点为node_n，第n+1个节点为end
3.连接链表，start.next = node_n,  node_m.next = end
4.返回头节点


#### 代码实现
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def reverseBetween(self, head: ListNode, m: int, n: int) -> ListNode:
        if not head or not head.next or m==n:
            return head
        dummy = ListNode(0)
        dummy.next = head
        start = dummy
        for i in range(m-1):
            start = start.next
                        
        end = cur = start.next  
        pre = None
        for i in range(n-m+1):
            next = cur.next
            cur.next = pre
            pre = cur
            cur = next            
        start.next = pre
        end.next = cur
        return dummy.next
```

本文链接：[https://www.jianshu.com/p/91b050e076b4](https://www.jianshu.com/p/91b050e076b4)
