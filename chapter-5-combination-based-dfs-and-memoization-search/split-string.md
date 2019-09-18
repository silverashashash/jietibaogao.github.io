## Split Spring

#### 字符串切割类

[http://www.lintcode.com/problem/split-string/](http://www.lintcode.com/problem/split-string/)



### Description

Give a string, you can choose to split the string after one character or two adjacent characters, and make the string to be composed of only one character or two characters. Output all possible results.

* 采用dfs解决此问题，每次向下递归时要么切割一个字符，要么切割两个字符。
- DFS: 构建一个dfs 辅助函数， 分别传入最终结果，中间变量path, 和字符串s，每次切割一个或者两个字母放入path，当切到字符串结尾就返回。



```py

#看了思路之后自己的答案
class Solution:
    """
    @param: : a string to be split
    @return: all possible split string array
    """

    def splitString(self, s):
        # write your code here
        if s is None:
            return []
        if len(s) == 0:
            return [[]]
            
        results = []
        self.dfs(s, [], results)
        return results
        
    def dfs(self, s, substrings, results):
        if len(s) == 0:
            results.append(list(substrings))
            return 
            
        for i in range(2):
            if i + 1 > len(s):
                break
            substrings.append(s[:i+1])
            
            self.dfs(s[i+1:], substrings, results)
            substrings.pop(） 

```

- 之前没想到的地方是，for循环里只要in range(2)就行了
- python里取字符串的技巧




```py
#九章里比较好的答案
#DFS: 构建一个dfs 辅助函数， 分别传入最终结果，中间变量path, 和字符串s，每次切割一个或者两个字母放入path，当切到字符串结尾就返回。
class Solution:
    def splitString(self, s):
        result = []
        self.dfs(result, [], s)
        return result 
    
    def dfs(self, result, path, s):
        if s == "":
            result.append(path[:]) #important: use path[:] to clone it
            return 
        for i in range(2):
            if i+1 <= len(s):
                path.append(s[:i+1])
                self.dfs(result, path, s[i+1:])
                path.pop()
```






