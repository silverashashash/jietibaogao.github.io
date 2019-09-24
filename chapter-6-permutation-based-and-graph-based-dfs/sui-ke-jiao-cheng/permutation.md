## Permutation 



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
- 视频教程里用visited[]数组记录访问过的下标，但是visited传入递归函数容易出错
