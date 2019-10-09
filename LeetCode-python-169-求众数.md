 [题目链接](https://leetcode-cn.com/problems/stone-game/description/)
难度： 简单          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：数组
***
给定一个大小为 n 的数组，找到其中的众数。众数是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在众数。
**示例1**
>输入: [3,2,3]
输出: 3

**示例2**
>输入: [2,2,1,1,1,2,2]
输出: 2
#### 解题思路
***
**思路1**：
先排序，再遍历数组统计次数，时间复杂度O（nlogn+n）

**思路2**：
直接遍历数组， candidate保存遍历的某个数，nTimes记录出现的次数。当遍历到数组中下一个数时：
    如果下一个数与candidate数一样，则nTimes+1
    如果下一个数与candidate数不一样，则nTimes-1
    如果nTimes变为0，则用candidate保存下一个数
    
 时间复杂度O(n).上述算法的理论是超过数组长度一般的数一定比其他所有数出现的次数总和多
#### 代码实现
```
def FindOneNumber(inputArray):
    length = len(inputArray)
    candidate = inputArray[0]
    nTimes = 1
    for i in range(1,length):
        if nTimes == 0:
            candidate = inputArray[i]
            nTimes = 1
        elif candidate == inputArray[i]:
            nTimes = nTimes + 1
        else:
            nTimes = nTimes - 1
    return candidate
```

本文链接：[https://www.jianshu.com/p/6091d6e28471](https://www.jianshu.com/p/6091d6e28471)
