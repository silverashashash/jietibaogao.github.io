## N Queens

[http://www.lintcode.com/problem/n-queens/](http://www.lintcode.com/problem/n-queens/)
[https://leetcode.com/problems/n-queens/](https://leetcode.com/problems/n-queens/)
n个皇后放在n*n的棋盘上，每个皇后不能在同一列、同一行、同一个对角线。求出所有可能解。

####思路
- 可以看成一个permutation的问题
- 不能同一行同一列表示n个数的排列不能出现重复
- 不能出现斜线攻击：斜线表示坐标(x,y)之差或者之和相等
- 判断条件较复杂时可以包装成一个函数`is_valid()`
- 用hashset并不会更快，因为n一般比较小，for循环基本可以看作$$O(1)$$。另一方面数组在内存中时连续存储，而哈希表是不连续存储。因此在调用哈希表的时候会花费较多时间内存寻址。
- 只有n很大的时候优化才有意义，但是这个问题上限是$$O(n!)$$，n很大没有意义。



####实现的问题
- output如何去实现？


```py
#竟然一遍就AC了，虽然是先看了教程，有了大概的思路
class Solution:
    """
    @param: n: The number of queens
    @return: All distinct solutions
    """
    def solveNQueens(self, n):
        # write your code here
        if n <= 0:
            return []
        results = []
        self.dfs(n, 0, [], [], results)
        return results
    
    def dfs(self, n, i, list_of_coord,  matrix, results):
        if len(matrix) == n:
            results.append(list(matrix))
            return 
        
        for j in range(n):
            coord_ = (i, j)
            if not self.is_valid(coord_, list_of_coord):
                continue
            
            array = self.make_array(n, coord_)
            list_of_coord.append(coord_)
            matrix.append(array)
            self.dfs(n, i + 1, list_of_coord, matrix, results)
            matrix.pop()
            list_of_coord.pop()
        
    def make_array(self, n, coord):
        array = ["."] * n
        array[coord[1]] = "Q"
        array = "".join(array)
        return array
    
    def is_valid(self, coord_new, list_of_coord):
        for coord_old in list_of_coord:
            if coord_new[0] == coord_old[0] or coord_new[1] == coord_old[1]:
                return False
            if coord_new[0] + coord_new[1] == coord_old[0] + coord_old[1] or coord_new[0] - coord_new[1] == coord_old[0] - coord_old[1]:
                return False
        return True
```
- Your submission beats 5.00% Submissions! 有没有优化的空间？

