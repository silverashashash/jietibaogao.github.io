## Split Spring

#### 字符串切割类

[http://www.lintcode.com/problem/split-string/](http://www.lintcode.com/problem/split-string/)



### Description

Give a string, you can choose to split the string after one character or two adjacent characters, and make the string to be composed of only one character or two characters. Output all possible results.

* 采用dfs解决此问题，每次向下递归时要么切割一个字符，要么切割两个字符。
- DFS: 构建一个dfs 辅助函数， 分别传入最终结果，中间变量path, 和字符串s，每次切割一个或者两个字母放入path，当切到字符串结尾就返回。




