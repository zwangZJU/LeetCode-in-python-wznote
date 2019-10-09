 [题目链接](https://leetcode-cn.com/problems/defanging-an-ip-address/)
难度：简单         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：  字符串
***
 给你一个有效的 [IPv4](https://baike.baidu.com/item/IPv4) 地址 `address`，返回这个 IP 地址的无效化版本。

所谓无效化 IP 地址，其实就是用 `"[.]"` 代替了每个 `"."`。


 
**示例1**
> 输入：address = "1.1.1.1"
输出："1[.]1[.]1[.]1"

**示例2**
>输入：address = "255.100.50.0"
输出："255[.]100[.]50[.]0"
 

#### 代码实现
```python
class Solution(object):
    def defangIPaddr(self, address):
        """
        :type address: str
        :rtype: str
        """
        return address.replace('.', '[.]')
```

本文链接：[https://www.jianshu.com/p/8a2cadf6b893](https://www.jianshu.com/p/8a2cadf6b893)
