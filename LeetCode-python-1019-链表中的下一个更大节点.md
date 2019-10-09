 [题目链接](https://leetcode-cn.com/problems/next-greater-node-in-linked-list/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  栈、链表
***
给出一个以头节点 head 作为第一个节点的链表。链表中的节点分别编号为：node_1, node_2, node_3, ... 。

每个节点都可能有下一个更大值（next larger value）：对于 node_i，如果其 next_larger(node_i) 是 node_j.val，那么就有 j > i 且  node_j.val > node_i.val，而 j 是可能的选项中最小的那个。如果不存在这样的 j，那么下一个更大值为 0 。

返回整数答案数组 answer，其中 answer[i] = next_larger(node_{i+1}) 。

注意：在下面的示例中，诸如 [2,1,5] 这样的输入（不是输出）是链表的序列化表示，其头节点的值为 2，第二个节点值为 1，第三个节点值为 5 。
 
**示例1**
> 输入：[2,1,5]
输出：[5,5,0]

**示例2**
>输入：[2,7,4,3,5]
输出：[7,0,5,5,0]

**示例3**
>输入：[1,7,5,1,9,2,5,1]
输出：[7,9,9,9,0,5,0,0]

#### 解题思路
***
 stack用于存储节点的序号index和节点的值val
res用于存储每个节点下一个更大的节点的值
遍历链表
若stack为空，直接进栈
若栈顶的val>当前节点的val，当前节点的序号和值进栈
若栈顶的val<当前节点的val，就找到的下一个更大的节点，在res[index]的位置存入当前节点的val，一直到栈为空或者栈顶val<当前节点的val



#### 代码实现
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def nextLargerNodes(self, head: ListNode) -> List[int]:
        res, stack, n = [], [], 0
        while head:
            
            while stack and stack[-1][1] < head.val:
                res[stack.pop()[0]] = head.val
            stack.append([n, head.val])
            res.append(0)
            n += 1
            head = head.next
        return res
                
```

本文链接：[https://www.jianshu.com/p/e646be06dcae](https://www.jianshu.com/p/e646be06dcae)
