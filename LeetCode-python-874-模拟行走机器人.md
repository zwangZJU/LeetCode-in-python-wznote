 [题目链接](https://leetcode-cn.com/problems/walking-robot-simulation/)
难度：简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  数组
***
 机器人在一个无限大小的网格上行走，从点 (0, 0) 处开始出发，面向北方。该机器人可以接收以下三种类型的命令：

-2：向左转 90 度
-1：向右转 90 度
1 <= x <= 9：向前移动 x 个单位长度
在网格上有一些格子被视为障碍物。

第 i 个障碍物位于网格点  (obstacles[i][0], obstacles[i][1])

如果机器人试图走到障碍物上方，那么它将停留在障碍物的前一个网格方块上，但仍然可以继续该路线的其余部分。

返回从原点到机器人的最大欧式距离的平方。
 
 
**示例1**
> 输入: commands = [4,-1,3], obstacles = []
输出: 25
解释: 机器人将会到达 (3, 4)

**示例2**
> 输入: commands = [4,-1,4,-2,4], obstacles = [[2,4]]
输出: 65
解释: 机器人在左转走到 (1, 8) 之前将被困在 (1, 4) 处

 
#### 解题思路
***
方向的描述有dx, dy完成，即向x和y轴移动的单位步长，只有四种d =  [(0, 1), (1, 0), (0, -1), (-1, 0)]，方向下标就为0，1，2，3.每次转向只是在相邻的下标里的一种，如初始为0，右转后就变为1，左转就变为-1，取模即可
模拟行走即可



#### 代码实现
```python
class Solution(object):
    def robotSim(self, commands, obstacles):
        """
        :type commands: List[int]
        :type obstacles: List[List[int]]
        :rtype: int
        """
        move = [(0, 1), (1, 0), (0, -1), (-1, 0)]
        obstacles = set(map(tuple, obstacles))
        cur_d = 0
        x, y = 0, 0
        max_dis = 0
        for c in commands:
            if c == -1:
                cur_d = (cur_d+1) % 4
            elif c == -2:
                cur_d = (cur_d-1) % 4
            else:
                dx, dy = move[cur_d]
                
                while c and (x+dx, y+dy) not in obstacles:     
                   # print([x+dx, y+dy])
                    x += dx
                    y += dy                 
                    c -= 1
            max_dis = max(max_dis, x**2+y**2)
        return max_dis
```

本文链接：[https://www.jianshu.com/p/bb807891fa2f](https://www.jianshu.com/p/bb807891fa2f)
