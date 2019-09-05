## Word Ladder

最典型的BFS：隐式图（Implicit Graph）最短路径  
[http://www.lintcode.com/problem/word-ladder/](http://www.lintcode.com/problem/word-ladder/)  
[https://leetcode.com/problems/word-ladder/](https://leetcode.com/problems/word-ladder/)  
本题不能用动态规划做，因为给出的点是无序的，找不出一个顺序进行for循环
骑士遍历可以用DP做，因为骑士有方向（向右走），可以写出状态转移方程
但是遇到这种简单图，用BFS解决比较简单

### Description

Given two words (_start_ and _end_), and a dictionary, find the shortest transformation sequence from _start_ to _end_, output the length of the sequence.  
Transformation rule such that:

1. Only one letter can be changed at a time
2. Each intermediate word must exist in the dictionary. \(Start and end words do not need to appear in the dictionary \)

```
- Return 0 if there is no such transformation sequence.
- All words have the same length.
- All words contain only lowercase alphabetic characters.
- You may assume no duplicates in the word list.
- You may assume beginWord and endWord are non-empty and are not the same.

```
- 隐式图，word是点，相应的transformation是边
- 本题需要用层级遍历
- 可以用``distance{}``记录``word:层数``，同时也可以查看word是否访问过。这样就不用size进行分层遍历了
- 用``get_next_word``函数得到邻居关系，办法是for这个word的每一位，换成a~z中另外的字符，凑成新单词，再检测这个单词在不在词典里。
    - check 一个单词在不在词典里的时间复杂度是$$O(L)$$, $$L$$为单词长度
