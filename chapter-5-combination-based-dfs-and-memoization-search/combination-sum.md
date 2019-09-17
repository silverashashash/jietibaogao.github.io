

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

