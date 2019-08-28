## 3Sum closest

Given an array`nums`of_n_integers and an integer`target`, find three integers in`nums` such that the sum is closest to `target`. Return the sum of the three integers. You may assume that each input would have exactly one solution.

**Example:**

```
Given array nums = [-1, 2, 1, -4], and target = 1.

The sum that is closest to the target is 2. (-1 + 2 + 1 = 2).

```

- 错误点1：[0,1,2], target=0 这里出错是因为循环c的时候范围是从0到len-1，应该是2到len-1
- 代码很繁琐，运行时间太长，寻找优化的办法


```py
#自己的代码
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        if not nums or len(nums) < 3:
            return None
        
        nums.sort()
        diff = sys.maxsize
        ans = sys.maxsize
        
        for i in range(len(nums)-1, 1, -1):
            lr = self.twosum_closest(nums, 0, i - 1, target - nums[i])
            if diff > abs(lr + nums[i] - target):
                ans = lr + nums[i]
                diff = abs(lr + nums[i] - target)
    
        return ans

    def twosum_closest(self, nums, start, end, target):
        if not nums or len(nums) < 2:
            return None
        
        diff = abs(nums[start] + nums[end] - target)
        ans = nums[start] + nums[end]
        
        while start < end:
            if nums[start] + nums[end] < target:
                if diff > abs(nums[start] + nums[end] - target):
                    diff = abs(nums[start] + nums[end] - target)
                    ans = nums[start] + nums[end]
                start += 1
            else:
                if diff > abs(nums[start] + nums[end] - target):
                    diff = abs(nums[start] + nums[end] - target)
                    ans = nums[start] + nums[end]              
                end -= 1
    
        return ans
                

```




```py
#九章答案

```



```
#leetcode上
class Solution:
    # @return an integer
    def threeSumClosest(self, num, target):
        num.sort()
        result = num[0] + num[1] + num[2]
        for i in range(len(num) - 2):
            j, k = i+1, len(num) - 1
            while j < k:
                sum = num[i] + num[j] + num[k]
                if sum == target:
                    return sum
                
                if abs(sum - target) < abs(result - target):
                    result = sum
                
                if sum < target:
                    j += 1
                elif sum > target:
                    k -= 1
            
        return result
```






  




