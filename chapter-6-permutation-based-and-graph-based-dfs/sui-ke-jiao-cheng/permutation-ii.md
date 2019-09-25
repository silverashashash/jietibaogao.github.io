## Permutation II

[https://www.lintcode.com/problem/permutations-ii/](https://www.lintcode.com/problem/permutations-ii/)

[https://leetcode.com/problems/permutations-ii/](https://leetcode.com/problems/permutations-ii/)  
有重复元素的排列

#### 思路：

* 重复是如何发生的？`[1,2,2]`
* 上面这两个重复元素要哪一个？
* 去重要在构造结果的过程中设计，而不是找到所有结果后去重
  * 通过排序筛选重复元素
  * 去重的通用方法就是选一个代表

```py
class Solution:
    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        if not nums:
            return []
        results = []
        visited = [0 for i in range(len(nums))]
        nums = sorted(nums)
        self.helper(nums, [], visited, results)
        return results

    def helper(self, nums, permutation, visited, results):
        if len(nums) == len(permutation):
            results.append(list(permutation))
            return

        for i in range(len(nums)):
            if i > 0 and nums[i] == nums[i - 1] and visited[i - 1] == 0:
                continue
            if visited[i] == 1:
                continue
            permutation.append(nums[i])
            visited[i] = 1
            self.helper(nums, permutation, visited, results)
            permutation.pop()
            visited[i] = 0
```

* 这道题必须用visited记录而不是简单的用in了
* 去重的时候也要看上一个是不是已访问的元素。



