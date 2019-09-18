## k Sum II
http://www.lintcode.com/problem/k-sum-ii/
找出k个数之和 = target的组合
#####注意下面这种代码量较少的写法，时间复杂度变高，因为会多出来复制list的时间 $$O(n)$$
```py
self.dfs(A, k, target, index + 1, onelist, anslist)
self.dfs(A, k, target - A[index], index + 1, onelist + [A[index]], anslist)
```


