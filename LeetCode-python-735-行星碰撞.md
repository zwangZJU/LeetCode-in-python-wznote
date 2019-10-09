 [题目链接](https://leetcode-cn.com/problems/asteroid-collision/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 数组，栈
***
 给定一个整数数组 asteroids，表示在同一行的行星。

对于数组中的每一个元素，其绝对值表示行星的大小，正负表示行星的移动方向（正表示向右移动，负表示向左移动）。每一颗行星以相同的速度移动。

找出碰撞后剩下的所有行星。碰撞规则：两个行星相互碰撞，较小的行星会爆炸。如果两颗行星大小相同，则两颗行星都会爆炸。两颗移动方向相同的行星，永远不会发生碰撞。

 
**示例1**
>输入: 
asteroids = [5, 10, -5]
输出: [5, 10]
解释: 
10 和 -5 碰撞后只剩下 10。 5 和 10 永远不会发生碰撞。

**示例2**
>输入: 
asteroids = [8, -8]
输出: []
解释: 
8 和 -8 碰撞后，两者都发生爆炸。

**示例3**
>输入: 
asteroids = [10, 2, -5]
输出: [10]
解释: 
2 和 -5 发生碰撞后剩下 -5。10 和 -5 发生碰撞后剩下 10。

**示例4**
>输入: 
asteroids = [-2, -1, 1, 2]
输出: [-2, -1, 1, 2]
解释: 
-2 和 -1 向左移动，而 1 和 2 向右移动。
由于移动方向相同的行星不会发生碰撞，所以最终没有行星发生碰撞。

#### 解题思路
***
先负后正，不发生碰撞
先正后负，发生碰撞
新建一个栈stack用于存储不发生碰撞以及碰撞完保留下来的行星

当栈顶元素top为正，下一个行星t为负时:
top>-t，结束碰撞
top<-t，top出栈，t继续与栈顶行星碰撞
top==-t，top出栈，结束碰撞

如果t为正：
直接入栈

#### 代码实现
```
class Solution:
    def asteroidCollision(self, asteroids: List[int]) -> List[int]:
        
        stack = []
        for i in range(len(asteroids)):
            t = asteroids[i]
          
            while stack and stack[-1]>0 and t<0: 
                if stack[-1]<-t:
                    stack.pop()
                    continue
                elif stack[-1] == -t:
                    stack.pop()
                break                        
            else:
                stack.append(t)
            
        return stack
```

本文链接：[https://www.jianshu.com/p/e0d14e85b302](https://www.jianshu.com/p/e0d14e85b302)
