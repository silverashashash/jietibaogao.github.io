## N Queens

[http://www.lintcode.com/problem/n-queens/](http://www.lintcode.com/problem/n-queens/)
[https://leetcode.com/problems/n-queens/](https://leetcode.com/problems/n-queens/)
n个皇后放在n*n的棋盘上，每个皇后不能在同一列、同一行、同一个对角线。求出所有可能解。

####思路
- 不能同一行同一列表示n个数的排列不能出现重复
- 不能出现斜线攻击：斜线表示坐标(x,y)之差或者之和相等
- 判断条件较复杂时可以包装成一个函数`is_valid`

