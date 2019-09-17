## Subsets 递归方式 （组合类）combination
关键字：所有方案
解决办法：DFS


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

####注意：
- list(subsets) 为什么要加list
这里牵扯到一个copy问题，如果不加list，那么copy的就是subset的reference，因此list之后的改变都会导致之前加入值的改变，加上list()之后就是建立了一个当前subset的copy，之后无论list如何改变，就不变了

