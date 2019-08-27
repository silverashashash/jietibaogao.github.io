## Merge  Sort

* 先往下递归直到变成最简单情况：只有一个数（input到子树里的是左右两边的数组）。这一个数是有序的。
* 每次返回**之后**要做的一件事是 merge two sorted list
* 所以merge\_sort的顺序是先递归，再merge two sorted list
* merge sort还要注意的是它会耗费额外空间，因此要传入一个temp数组



