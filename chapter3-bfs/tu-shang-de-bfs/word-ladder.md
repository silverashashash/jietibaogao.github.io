## Word Ladder

最典型的BFS：隐式图（Implicit Graph）最短路径  
[http://www.lintcode.com/problem/word-ladder/](http://www.lintcode.com/problem/word-ladder/)  
[https://leetcode.com/problems/word-ladder/](https://leetcode.com/problems/word-ladder/)  
本题不能用动态规划做，因为给出的点是无序的  
骑士遍历可以用DP做，因为棋子可以向任何方向移动，可以写出状态转移方程

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

``

