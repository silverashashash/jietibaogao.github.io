## Combination Sum
http://www.lintcode.com/problem/combination-sum/


####与 Subsets 比较
- Combination Sum 限制了组合中的数之和 
    - 加入一个新的参数来限制
- Subsets 无重复元素，Combination Sum 有重复元素
    -需要先去重
        - candidates 先去重 `candidates = sorted(list(set(candidates)))`
- Subsets 一个数只能选一次，Combination Sum 一个数可以选很多次
    - 搜索时从 index 开始而不是从 index + 1
        - 通过入target比较防止无限循环下去
    
    
```py
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        if candidates is None:
            return []
        results = []
        subset = []
        
        self.dfs(candidates, 0, target, subset, results)
        return results
    
    def dfs(self, candidates, start_index, target, subset, results):
        if sum(subset) == target:
            results.append(list(subset))
        if sum(subset) > target:
            return 
        
        for i in range(start_index, len(candidates)):
            subset.append(candidates[i])
            self.dfs(candidates, i, target, subset, results)
            subset.pop()
        
        
```

