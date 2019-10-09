 [题目链接](https://leetcode-cn.com/problems/linked-list-cycle/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：链表  
***
 给定一个链表，判断链表中是否有环。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。

 
 
#### 解题思路
***
 快慢指针，快的一次走两步，慢的一次走一步，若有环，两指针会相遇



#### 代码实现
```
class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        slow = head
        fast = head
        while slow and fast:
            fast = fast.next
            if fast == slow:
                return True
            if fast:
                fast = fast.next
                if fast == slow:
                    return True
            slow = slow.next
        return False
```

本文链接：[https://www.jianshu.com/p/1fada0732034](https://www.jianshu.com/p/1fada0732034)
