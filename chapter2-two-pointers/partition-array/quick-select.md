## Quick select

见随课教程

* quicksort要把等于的情况单独拿出来讨论，是为了避免在数组元素一样时，退化成$$O(n^2)$$
* offline Algorithm:  完全给定了输入之后在$$O(n)$$ 时间内不用排序，找到从小到大第k个数


``quick-select`` 是``quick-sort``其中的一个步骤。主要用来解决``kth-largest-element``类的题
如果先排序再数到第k个数，则会花费$$O(nlogn)$$的复杂度。
一个更快的方法就是用``quick-select``。
另一道类似的题时``Median``（寻找中位数），即``k=N/2``



```
#Time Complexity：

```







