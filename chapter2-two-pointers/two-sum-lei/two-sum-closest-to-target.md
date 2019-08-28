## Two sum - closest to target

### Description

Given an array`nums`of _n_ integers, find two integers in ``nums`` such that the sum is closest to a given number, ``target``.

Return the absolute value of difference between the sum of the two integers and the target.

### Example

**Example1**

```
Input:  nums = [-1, 2, 1, -4] and target = 4
Output: 1
Explanation:
The minimum difference is 1. (4 - (2 + 1) = 1).
```

**Example2**

```
Input:  nums = [-1, -1, -1, -4] and target = 4
Output: 6
Explanation:
The minimum difference is 6. (4 - (- 1 - 1) = 6).
```

### Challenge

Do it in O\(nlogn\) time complexity.

* 用一个数去记录difference
- 这也是研究两个变量如何组合的问题，循环其中一个变量，研究另一个的变化
6




```py
class Solution:
    """
    @param nums: an integer array
    @param target: An integer
    @return: the difference between the sum and the target
    """
    def twoSumClosest(self, nums, target):
        # write your code here
        
        if not nums or len(nums) < 2:
            return None
            
        nums.sort()
        # diff 
        
        l, r = 0, len(nums) - 1 
        diff = abs(nums[l]+nums[r]-target)
        
        while l + 1 < r:
            if l + 1 < r  and nums[l] + nums[r] > target:
                r -= 1
                diff = min(abs(nums[l]+nums[r]-target),diff)
            elif l + 1< r  and nums[l] + nums[r] < target:
                l += 1
                diff = min(abs(nums[l]+nums[r]-target),diff)
            else:
                return 0
        return diff

```

自己的思路是两个指针相向而行，每次移动指针都计算一下sum和target之差，一旦符号变换则换另一个指针。因为时排序数组，所以sum-target的最小值肯定出现在正负号变换的时候。

- 错误点1: left 和right总有机会相交，也就是left == right的情况，怎么排除掉？如果用left + 1 < right， 则会run out of time。 
    - 解决办法：用二分法模板里的start + 1 < end
- 错误点2: 一开始我认为循环退出时左右两指针的位置就是sum-target最小值的位置。实际上循环退出的条件是left和right相遇，所以最小值出现在其中某次符号变换的时候，而不是最后一次或者left和right相遇的时候。所以每次移动指针都要记录下一个最小值。

