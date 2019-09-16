## Closest Binary Search Tree Value
- 如果使用中序遍历（非递归），时间复杂度是多少？ $$O(n+logn)$$, 但有$$O(n)$$的额外空间消耗
- 如果使用lowerBound/upperBound的方法，时间复杂度是多少？

https://www.lintcode.com/problem/closest-binary-search-tree-value/

- 类似 kth closest
- 使用非递归版本
- 中序遍历$$O(n)$$ + BST $$O(logn)$$ = $$O(n + log n)$$，但有$$O(n)$$的额外空间
 
 
 ```py
 Class Solution:
 
 
 ```