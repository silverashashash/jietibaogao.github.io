## k Sum II
http://www.lintcode.com/problem/k-sum-ii/
找出k个数之和 = target的组合
#####注意下面这种代码量较少的写法，时间复杂度变高，因为会多出来复制list的时间 $$O(n)$$
```py
self.dfs(A, k, target, index + 1, onelist, anslist)
self.dfs(A, k, target - A[index], index + 1, onelist + [A[index]], anslist)
```




```py
class Solution:
    """
    @param: A: an integer array
    @param: k: a postive integer <= length(A)
    @param: targer: an integer
    @return: A list of lists of integer
    """
    def kSumII(self, A, k, target):
        # write your code here
        if A is None:
            return []
        if A == []:
            return [[]]
        
        subset = []
        results = []
        A = sorted(list(set(A)))
        self.dfs(A, k, target, 0, subset, results)
        return results
        
    def dfs(self, A, k, target, start_index, subset, results):
        if sum(subset) == target and k == 0:
            results.append(list(subset))
        if sum(subset) > target or k < 0:
            return 
        for i in range(start_index, len(A)):
            subset.append(A[i])
            self.dfs(A, k - 1, target, i + 1, subset, results)
            subset.pop()

```
- ``if len(A) == 0``可以加在dfs函数里的if中，这样就不用在开头写那个corner case了
