 [题目链接](https://leetcode-cn.com/problems/keys-and-rooms/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  广度优先搜索
***
有 N 个房间，开始时你位于 0 号房间。每个房间有不同的号码：0，1，2，...，N-1，并且房间里可能有一些钥匙能使你进入下一个房间。

在形式上，对于每个房间 i 都有一个钥匙列表 rooms[i]，每个钥匙 rooms[i][j] 由 [0,1，...，N-1] 中的一个整数表示，其中 N = rooms.length。 钥匙 rooms[i][j] = v 可以打开编号为 v 的房间。

最初，除 0 号房间外的其余所有房间都被锁住。

你可以自由地在房间之间来回走动。

如果能进入每个房间返回 true，否则返回 false。

 
**示例1**
> 输入: [[1],[2],[3],[]]
输出: true
解释:  
我们从 0 号房间开始，拿到钥匙 1。
之后我们去 1 号房间，拿到钥匙 2。
然后我们去 2 号房间，拿到钥匙 3。
最后我们去了 3 号房间。
由于我们能够进入每个房间，我们返回 true。

**示例2**
>输入：[[1,3],[3,0,1],[2],[0]]
输出：false
解释：我们不能进入 2 号房间。

#### 解题思路
***
 1. 初始化时进到第0个房间，拿到所有的钥匙，放在queue里，rooms[0]置为False
2. 进到queue里所有的房间，进过的房间都出queue, 拿到所有进过的房间里面的钥匙再存入queue，将该房间设为False，代表已经进去过，下次再拿到该房间的钥匙也不用进去了
3. 重复第二步，直到queue里所有的房间都去过，即queue为空
4. 若room中有不为False的，就说明没进去过，返回False，否则返回True

例如：[[1,3],[3,0,1],[2],[0]]
初始化queue=[1,3], rooms = [False,[3,0,1],[2],[0]]
1. 1出queue,[3,0,1]进queue, queue=[3,3,0,1],  rooms = [False,False,[2],[0]]
2. 3出queue，[0]进queue, queue=[3,0,1,0],  rooms = [False,False,[2],False]
3. 3出queue，queue=[0,1,0],  rooms = [False,False,[2],False]
4. 0出queue，queue=[1,0],  rooms = [False,False,[2],False]
5. 1出queue，queue=[0],  rooms = [False,False,[2],False]
6. 0出queue，queue=[],  rooms = [False,False,[2],False]
此时queue为空，rooms不全为False，返回False

#### 代码实现
```python
class Solution(object):
    def canVisitAllRooms(self, rooms):
        """
        :type rooms: List[List[int]]
        :rtype: bool
        """
        queue, rooms[0] = rooms[0], False
        while queue:
            k = queue.pop(0)
            if rooms[k]:
                queue.extend(rooms[k])
                rooms[k] = False       
        return not any(rooms)
```

本文链接：[https://www.jianshu.com/p/635255a712c6](https://www.jianshu.com/p/635255a712c6)
