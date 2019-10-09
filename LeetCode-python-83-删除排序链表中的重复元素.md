 [题目链接](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list/)
难度：简单      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
 给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次。

 
**示例1**
> 输入: 1->1->2
输出: 1->2

**示例2**
>输入: 1->1->2->3->3
输出: 1->2->3

#### 解题思路
***
如果当前节点的值和下一个节点的值相等，则当前节点的下一个节点修改为当前节点下一个节点的下一个节点 



#### 代码实现
```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head: return head
        dummy = head
        while head.next:
            if head.val == head.next.val:
                head.next = head.next.next
            else:
                head = head.next
        return dummy
```

本文链接：[https://www.jianshu.com/p/49c51ea22bdb](https://www.jianshu.com/p/49c51ea22bdb)

 
