## Permutation 
https://www.lintcode.com/problem/permutations/
https://leetcode.com/problems/permutations/
无重复元素的排列
```py
#根据上一章的Combination模板
class Solution:
    def permute(self, nums: List[int]) -> List[List[int]]:
        if not nums:
            return []
        results = []
        self.helper(nums, [], results)
        return results
    
    def helper(self, nums, permutation, results):
        if len(nums) == len(permutation):
            results.append(list(permutation))
            return
        
        for i in range(len(nums)):
            if nums[i] in permutation:
                continue
            permutation.append(nums[i])
            self.helper(nums, permutation, results)
            permutation.pop()        
```

#### 或者学java用一个visited[]数组记录访问过的下标

```py
class Solution:
    """
    @param: nums: A list of integers.
    @return: A list of permutations.
    """
    def permute(self, nums):
        # write your code here
        results = []
        if not nums:
            return results
        permutation = []
        visited = [False for i in range(len(nums))]
        self.dfs(nums, permutation, results, visited)
        return results

    def dfs(self, nums, permutation, results, visited):

          if len(nums) == len(permutation):
            results.append(list(permutation))
            return 

          for i in range(len(nums)):
            if visited[i]:
                 continue
            permutation.append(nums[i])
            visited[i] = True
            self.dfs(nums, permutation, results, visited)
            visited[i] = False
            permutation.pop()


```


