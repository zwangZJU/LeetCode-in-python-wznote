 [题目链接](https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/)
难度：中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  递归
***
 给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。

给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

![](https://upload-images.jianshu.io/upload_images/15048949-7517fe2729b6dcce.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)



 
**示例**
> 输入："23"
输出：["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].

#### 解题思路
***
 当没有数字的时候返回空
当只有一个数字的时候，返回该数字对应的字母
当有两个数字的时候，返回第一个数字对应的字母分别加上第二个数字所对应的字母，生成字符串列表
当有三个数字的时候，返回第一个数字对应的字母分别奸商后两个数字生成的字符串列表

#### 代码实现
```python
class Solution(object):
    def letterCombinations(self, digits):
        """
        :type digits: str
        :rtype: List[str]
        """
        dic = {
            '2':['a', 'b', 'c'],
            '3':['d', 'e', 'f'],
            '4':['g', 'h', 'i'],
            '5':['j', 'k', 'l'],
            '6':['m', 'n', 'o'],
            '7':['p', 'q', 'r', 's'],
            '8':['t', 'u', 'v'],
            '9':['w', 'x', 'y', 'z']
        }
        result = []
        tail = []
        len_d = len(digits)
        if len_d == 0:
            return tail
        if len_d == 1:
            return dic[digits]
        
        tail = self.letterCombinations(digits[1:])
        
        for i in dic[digits[0]]:
            for j in tail:
                result.append(i+j)
        return result
            
```

本文链接：[https://www.jianshu.com/p/4988ca29bfce](https://www.jianshu.com/p/4988ca29bfce)
