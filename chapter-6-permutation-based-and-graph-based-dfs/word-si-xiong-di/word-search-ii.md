## Word Search II
http://www.lintcode.com/problem/word-search-ii/ 
矩阵(Matrix)也是图

- 以前说过，矩阵也是图
- 找的是路径而不是点，因此要backtracking
- for 循环起始位置，找到从这个位置出发有哪些单词
- 搜索的时候参数较多：棋盘、xy坐标、word、word_set、单词前缀set、visited的点、results


 