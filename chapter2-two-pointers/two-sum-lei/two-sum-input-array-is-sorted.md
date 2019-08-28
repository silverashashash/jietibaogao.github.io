## Two Sum-II input array is sorted

Given an array of integers that is already _**sorted in ascending order**_, find two numbers such that they add up to a specific target number.

The function twoSum should return indices of the two numbers such that they add up to the target, where index1 must be less than index2.

**Note:**

* Your returned answers \(both index1 and index2\) are not zero-based.
* You may assume that each input would have \_exactly \_one solution and you may not use the \_same \_element twice.

**使用 two pointers而不用hashmap是因为前者更快。**

开辟额外空间也需要时间, sorted array 的话用two pointers时间复杂度就是$$O(n)$$了

|  | Time Complexity | Space Complexity |
| :--- | :--- | :--- |
| Hash | $$O(n)$$ | $$O(n)$$ |
| Two Pointers | $$O(logn)$$ 要先排序 | $$O(1)$$ |

```py
#自己的答案：
class Solution(object):
    def twoSum(self, numbers, target):
        """
        :type numbers: List[int]
        :type target: int
        :rtype: List[int]
        """
        if not numbers:
            return None

        left, right = 0, len(numbers)-1

        for left in range(len(numbers)):
            while left < right and numbers[left] + numbers[right] > target:
                right -= 1
            if numbers[left] + numbers[right] == target:
                return [left + 1, right + 1]

        return[-1, -1]
```

* Runtime: 48 ms, faster than 71.34% of Python online submissions for Two Sum II - Input array is sorted. Memory Usage:  12.3 MB, less than 16.36% of Python online submissions for Two Sum II - Input array is sorted.

* 自己的做法感觉并没有用到two pointers的优越性？

* 因为这已经是个排序数组了，并且存在唯一解。所以在nums\[left\]+nums\[right\] &gt; target时只能移动right才能找到可能解。

```py
#九章答案
class Solution:
    """
    @param nums {int[]} n array of Integer
    @param target {int} = nums[index1] + nums[index2]
    @return {int[]} [index1 + 1, index2 + 1] (index1 < index2)
    """
    def twoSum(self, nums, target):
        # Write your code here
        l, r = 0, len(nums)-1
        while l < r:
            value = nums[l] + nums[r]
            if value == target:
                return [l+1, r+1]
            elif value < target:
                l += 1
            else:
                r -= 1
        return []
```

* Runtime:  40 ms, faster than 97.84% of Python online submissions for Two Sum II - Input array is sorted. Memory Usage:  11.9 MB , less than 90.91% of Python online submissions for Two Sum II - Input array is sorted.



