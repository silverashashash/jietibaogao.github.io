## Closest Binary Search Tree Value
- 如果使用中序遍历（非递归），时间复杂度是多少？ $$O(n+logn)$$, 但有$$O(n)$$的额外空间消耗
- 如果使用lowerBound/upperBound的方法，时间复杂度是多少？

https://www.lintcode.com/problem/closest-binary-search-tree-value/

- 类似 kth closest
- 使用非递归版本
- 中序遍历$$O(n)$$ + BST $$O(logn)$$ = $$O(n + log n)$$，但有$$O(n)$$的额外空间
 
 
 ####思路：
算法很简单，求出 lowerBound 和 upperBound(上下边界)。即 < target 的最大值和 >= target 的最小值。
然后在两者之中去比较谁更接近，然后返回即可。

时间复杂度为 $$O(h)$$，注意如果你使用 in-order traversal 的化，时间复杂度会是 o(n)o(n) 并不是最优的。另外复杂度也不是 $$O(logn)$$ 因为BST 并不保证树高是 $$logn$$的。
 
 
 4153447593
 
 ```py
 Class Solution:
 
 
 ```