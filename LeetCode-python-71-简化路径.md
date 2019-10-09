 [题目链接](https://leetcode-cn.com/problems/simplify-path/)
难度： 中等          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;类型：字符串
***
以 Unix 风格给出一个文件的**绝对路径**，你需要简化它。或者换句话说，将其转换为规范路径。

在 Unix 风格的文件系统中，一个点（`.`）表示当前目录本身；此外，两个点 （`..`） 表示将目录切换到上一级（指向父目录）；两者都可以是复杂相对路径的组成部分。更多信息请参阅：[Linux / Unix中的绝对路径 vs 相对路径](https://blog.csdn.net/u011327334/article/details/50355600)

请注意，返回的规范路径必须始终以斜杠 `/` 开头，并且两个目录名之间必须只有一个斜杠 `/`。最后一个目录名（如果存在）**不能**以 `/` 结尾。此外，规范路径必须是表示绝对路径的**最短**字符串。

**示例1**
>输入："/home/"
输出："/home"
解释：注意，最后一个目录名后面没有斜杠。

**示例2**
>输入："/../"
输出："/"
解释：从根目录向上一级是不可行的，因为根是你可以到达的最高级。

**示例3**
>输入："/home//foo/"
输出："/home/foo"
解释：在规范路径中，多个连续斜杠需要用一个斜杠替换。

**示例4**
>输入："/a/./b/../../c/"
输出："/c"

**示例5**
>输入："/a/../../b/../c//.//"
输出："/c"

#### 解题思路
***
用‘/’ split 字符串 成 字符数组strs
若strs[i]为字符串，入栈
若strs[i]为‘.'，不做任何操作
若strs[i]为’..', 且栈不为空，栈顶元素pop掉
遍历完整个数组后
将栈中元素拼接成字符串，用‘/’分隔

#### 代码实现
```
class Solution:
    def simplifyPath(self, path):
        """
        :type path: str
        :rtype: str
        """
        dirs = path.split('/')
        res = []
        for d in dirs:
            if d:                 
                if d == '..':
                    if res:
                        res.pop(-1)
                elif d != '.':
                    res.append(d)       
        return '/'+'/'.join(res)
```

本文链接：[https://www.jianshu.com/p/4da8fffe09be](https://www.jianshu.com/p/4da8fffe09be)
