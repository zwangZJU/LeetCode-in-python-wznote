 [题目链接](https://leetcode-cn.com/problems/lru-cache/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  哈希表
***
 运用你所掌握的数据结构，设计和实现一个  LRU (最近最少使用) 缓存机制。它应该支持以下操作： 获取数据 get 和 写入数据 put 。

获取数据 get(key) - 如果密钥 (key) 存在于缓存中，则获取密钥的值（总是正数），否则返回 -1。
写入数据 put(key, value) - 如果密钥不存在，则写入其数据值。当缓存容量达到上限时，它应该在写入新数据之前删除最近最少使用的数据值，从而为新的数据值留出空间。

进阶:

你是否可以在 O(1) 时间复杂度内完成这两种操作？
 
 
**示例**
> LRUCache cache = new LRUCache( 2 /* 缓存容量 */ );
cache.put(1, 1);
cache.put(2, 2);
cache.get(1);       // 返回  1
cache.put(3, 3);    // 该操作会使得密钥 2 作废
cache.get(2);       // 返回 -1 (未找到)
cache.put(4, 4);    // 该操作会使得密钥 1 作废
cache.get(1);       // 返回 -1 (未找到)
cache.get(3);       // 返回  3
cache.get(4);       // 返回  4

 
#### 解题思路
***
哈希表的存储是无序的，用OrderedDict() ，可以做到有序存储，存储的顺序按照进入字典的顺序
通过pop(key)可以得到key所对应的value
popitem()可以的到最后一个进表的value，而popitem(last=False)可以得到第一个进表的value



#### 代码实现
```python
import collections
class LRUCache:

    def __init__(self, capacity: int):
        self.capacity = capacity         
        self.catch = collections.OrderedDict()
        

    def get(self, key: int) -> int:
        if key not in self.catch:
            return -1
       
        value = self.catch.pop(key)
        self.catch[key] = value
        return value

    def put(self, key: int, value: int) -> None:
        if key in self.catch:
            self.catch.pop(key)
        elif self.catch and self.capacity == 0:
            self.catch.popitem(last=False)
        else:
            self.capacity -= 1
        self.catch[key] = value 
```

本文链接：[https://www.jianshu.com/p/77d14cf02196](https://www.jianshu.com/p/77d14cf02196)
