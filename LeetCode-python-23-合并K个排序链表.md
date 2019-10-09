 [题目链接](https://leetcode-cn.com/problems/merge-k-sorted-lists/)
难度： 困难          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：链表
***
合并 k 个排序链表，返回合并后的排序链表。请分析和描述算法的复杂度。

**示例**
>输入:
[
  1->4->5,
  1->3->4,
  2->6
]
输出: 1->1->2->3->4->4->5->6

#### 解题思路
***
将k个链表建立成一个最小堆，再从堆顶pop()出每一个元素，连接成链表

**heapq是python的内置模块，介绍几个简单的用法：**
heap.heapify(x): 将x （list 类型） 转化成最小堆，in-place， 时间复杂度O(len(x))
heap.heappop(heap): 返回root节点，即heap中最小的元素 


#### 代码实现
```
import heapq
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeKLists(self, lists):
        """
        :type lists: List[ListNode]
        :rtype: ListNode
        """
        nums = []
        for l in lists:
            while l:
                nums.append(l.val)
                l = l.next
        heapq.heapify(nums)
        head = ListNode(0)
        cur = head
        while nums:
            cur.next = ListNode(heapq.heappop(nums))
            cur = cur.next
        return head.next
            
```

本文链接：[https://www.jianshu.com/p/5b7bd4dd39c3](https://www.jianshu.com/p/5b7bd4dd39c3)
