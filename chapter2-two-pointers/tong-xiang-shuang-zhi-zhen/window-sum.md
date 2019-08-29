## Window sum

### Description

Given an array of n integers, and a moving window\(size k\), move the window at each iteration from the start of the array, find the`sum`of the element inside the window at each moving.

Have you met this question in a real interview?

**Example 1**

```
Input：array = [1,2,7,8,5], k = 3
Output：[10,17,20]
Explanation：
1 + 2 + 7 = 10
2 + 7 + 8 = 17
7 + 8 + 5 = 20
```



```py
#自己的答案
class Solution:
    """
    @param nums: a list of integers.
    @param k: length of window.
    @return: the sum of the element inside the window at each moving.
    """
    def winSum(self, nums, k):
        # write your code here
            
        result = []
        if not nums or len(nums) < k:
            return result
        
        sum = 0
        for i in range(0,k):
            sum += nums[i]
        result.append(sum)
        
        for j in range(k,len(nums)):
            sum = sum + nums[j] - nums[j-k]
            result.append(sum)
            
        return result
```


```py
#九章的答案
class Solution:
    # @param nums {int[]} a list of integers
    # @param k {int} size of window
    # @return {int[]} the sum of element inside the window at each moving
    def winSum(self, nums, k):
        # Write your code here
        n = len(nums)
        if n < k or k <= 0:
            return []
        sums = [0] * (n - k + 1)
        for i in range(k):
            sums[0] += nums[i];

        for i in range(1, n - k + 1):
            sums[i] = sums[i - 1] - nums[i - 1] + nums[i + k - 1]

        return sums
```





