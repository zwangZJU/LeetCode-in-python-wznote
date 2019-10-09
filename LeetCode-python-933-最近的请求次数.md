 [题目链接](https://leetcode-cn.com/problems/number-of-recent-calls/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  队列
***
 写一个 RecentCounter 类来计算最近的请求。

它只有一个方法：ping(int t)，其中 t 代表以毫秒为单位的某个时间。

返回从 3000 毫秒前到现在的 ping 数。

任何处于 [t - 3000, t] 时间范围之内的 ping 都将会被计算在内，包括当前（指 t 时刻）的 ping。

保证每次对 ping 的调用都使用比之前更大的 t 值。

 
 
**示例**
> 输入：inputs = ["RecentCounter","ping","ping","ping","ping"], inputs = [[],[1],[100],[3001],[3002]]
输出：[null,1,2,3,3]

 
 
#### 代码实现
```python
class RecentCounter(object):

    def __init__(self):
        self.queue = []

    def ping(self, t):
        """
        :type t: int
        :rtype: int
        """
        self.queue.append(t)
        while self.queue[0]<t-3000:
            self.queue.pop(0)   
        return len(self.queue)
```

本文链接：[https://www.jianshu.com/p/175818fe2b07](https://www.jianshu.com/p/175818fe2b07)
