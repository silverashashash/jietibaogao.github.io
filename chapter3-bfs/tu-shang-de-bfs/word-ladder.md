##Word Ladder
最典型的BFS：隐式图（Implicit Graph）最短路径
http://www.lintcode.com/problem/word-ladder/
https://leetcode.com/problems/word-ladder/
本题不能用动态规划做，因为给出的点是无序的
骑士遍历可以用DP做，因为棋子可以向任何方向移动，可以写出状态转移方程