## Subsets 递归方式 （组合类）



```py
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        self.result = []
        # subset = []
        # if nums is None:
        #     return []
        
        nums = sorted(nums)
        self.dfs(nums, 0, [])
        
        return self.result
    
    def dfs(self, nums, index, subset):

        if index == len(nums):
            self.result.append(list(subset))
            return
        
        subset.append(nums[index])
        self.dfs(nums, index + 1, subset)
        
        subset.pop()
        self.dfs(nums, index + 1, subset)
        
        
        
```

