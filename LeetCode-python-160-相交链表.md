[题目链接](https://leetcode-cn.com/problems/intersection-of-two-linked-lists/)

难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  链表
***
 编写一个程序，找到两个单链表相交的起始节点。

**示例**
![](https://upload-images.jianshu.io/upload_images/15048949-2438de67d34dc295.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
#### 解题思路
***
双指针：
两个指针p1、p2分别指向链表A、B的头节点，两个指针每次同时向前移动一步，比较p1是否等于p2，相等时即为相交节点
若p1指向链表尾端时还未相等,就把p1放到B的头节点,同理，p2在移动到尾端时，把p2放在A的头节点，继续同时移动，若有交点，必定会有p1==p2，若p1=p2=NULL，则没有交点


#### 代码实现
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type head1, head1: ListNode
        :rtype: ListNode
        """
        p1 = headA
        p2 = headB
        while p1!=p2:
            if not p1:
                p1 = headB
            else:
                p1 = p1.next
            if not p2:
                p2 = headA
            else:
                p2 = p2.next
        return p1
```

本文链接：[https://www.jianshu.com/p/17347c6768fa](https://www.jianshu.com/p/17347c6768fa)
