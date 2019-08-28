## Two sum 计数：two sum less than or equal to target

### Description

Given an array of integers, find how many pairs in the array such that their sum is`less than or equal to`a specific target number. Please return the number of pairs.

Example 1:

```
Input: nums = [2, 7, 11, 15], target = 24. 
Output: 5. 
Explanation:
2 + 7 < 24
2 + 11 < 24
2 + 15 < 24
7 + 11 < 24
7 + 15 < 24
```

Example 2:

```
Input: nums = [1], target = 1. 
Output: 0.
```

* 对于求两个变量如何组合的问题，可以循环其中一个变量，然后研究另外一个变量如何变化(课件)
* 和trianlge count是差不多的题


```py
#自己的答案（和九章的差不多）
class Solution:
    """
    @param nums: an array of integer
    @param target: an integer
    @return: an integer
    """
    def twoSum5(self, nums, target):
        # write your code here
        if not nums or len(nums) < 2:
            return 0
        n = 0
        nums.sort()
        
        left, right = 0, len(nums) - 1 
        while left < right:
            if nums[left] + nums[right] > target:
                right -= 1 
            
            else:
                n += right - left
                left += 1 
            
        return n 
```





