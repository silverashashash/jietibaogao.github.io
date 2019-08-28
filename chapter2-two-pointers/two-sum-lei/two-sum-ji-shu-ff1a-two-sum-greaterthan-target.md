## Two sum 计数：two sum greater than target



Given an array of integers, find how many pairs in the array such that their sum is bigger than a specific target number. Please return the number of pairs.

### Example

**Example 1:**

```
Input: [2, 7, 11, 15], target = 24
Output: 1
Explanation: 11 + 15 is the only pair.

```

**Example 2:**

```
Input: [1, 1, 1, 1], target = 1
Output: 6

```

### Challenge

Do it in O\(1\) extra space and O\(nlogn\) time.



```py
#和上一题一样
class Solution:
    """
    @param nums: an array of integer
    @param target: An integer
    @return: an integer
    """
    def twoSum2(self, nums, target):
        # write your code here
        
        if not nums or len(nums) < 2:
            return 0
            
        n = 0 
        nums.sort()
        
        left, right = 0, len(nums) - 1 
        
        while left < right:
            if nums[left] + nums[right] > target:
                n += right - left
                right -= 1 
            else:
                left += 1 
        
        return n 
```









