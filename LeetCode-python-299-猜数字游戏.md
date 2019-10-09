 [题目链接](https://leetcode-cn.com/problems/bulls-and-cows/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型： 哈希表 
***
你正在和你的朋友玩 猜数字（Bulls and Cows）游戏：你写下一个数字让你的朋友猜。每次他猜测后，你给他一个提示，告诉他有多少位数字和确切位置都猜对了（称为“Bulls”, 公牛），有多少位数字猜对了但是位置不对（称为“Cows”, 奶牛）。你的朋友将会根据提示继续猜，直到猜出秘密数字。

请写出一个根据秘密数字和朋友的猜测数返回提示的函数，用 A 表示公牛，用 B 表示奶牛。

请注意秘密数字和朋友的猜测数都可能含有重复数字。

 
**示例1**
> 输入: secret = "1807", guess = "7810"
输出: "1A3B"
解释: 1 公牛和 3 奶牛。公牛是 8，奶牛是 0, 1 和 7。

**示例2**
> 输入: secret = "1123", guess = "0111"
输出: "1A1B"
解释: 朋友猜测数中的第一个 1 是公牛，第二个或第三个 1 可被视为奶牛。
 

#### 解题思路
***
 逐位去猜，有两种结果：猜的数字在secret里，或者不在；在secret里又分两种：位置对和位置不对，位置对的很容易找，同时遍历两个字符串就可以

统计secret和guess中字符的频率，累加共有的字符中频率更小的一个作为猜到的，如示例2中的‘1’，共有的就取min(2,3)

A的个数是数字相同且位置对的个数，B的个数为相同数字的个数-A的个数



#### 代码实现
```python
class Solution(object):
    def getHint(self, secret, guess):
        """
        :type secret: str
        :type guess: str
        :rtype: str
        """
        a = 0
        ds, dg = {}, {}
        for i in range(len(secret)):
            if secret[i] == guess[i]:
                a += 1
            ds[secret[i]] = ds[secret[i]] + 1 if secret[i] in ds else 1
            dg[guess[i]] = dg[guess[i]] + 1 if guess[i] in dg else 1
             
        correct = 0
        for item in ds:
            if item in dg:
                correct += min(ds[item], dg[item])

        return str(a)+'A'+str(correct-a)+'B'
```

本文链接：[https://www.jianshu.com/p/9b31c3a63071](https://www.jianshu.com/p/9b31c3a63071)
