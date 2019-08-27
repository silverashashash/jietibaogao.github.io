## Two sum - unique pair

###Description

Given an array of integers, find how many unique pairs in the array such that their sum is equal to a specific target number. Please return the number of pairs.

- 找到之后继续寻找，也就是移动指针的时候判断是否已经遇到过了

问题：可否先去重？去重的代码更麻烦（太多if else）

```py
#自己的代码
class Solution:
    """
    @param nums: an array of integer
    @param target: An integer
    @return: An integer
    """
    def twoSum6(self, nums, target):
        # write your code here
        if not nums:
            return 0
        
        n = 0 
        left, right = 0, len(nums) - 1 
        
        nums.sort()
        
        while left < right:
            if nums[left] + nums[right] == target:
                while left < right and nums[left] == nums[left+1]:
                    left += 1
                while left < right and nums[right] == nums[right-1]:
                    right -= 1 
                n += 1
                left += 1
                right -= 1 
            elif nums[left] + nums[right] > target:
                right -= 1 
            else:
                left += 1 
        
        return n 
```

- 调用``sort()``的时候用成``self.sort(nums)`` ``self.nums.sort()``了。``sort``是外部函数，可以直接调用。只有自己定义的函数才需要用``self``。
- 刚开始超时了，原因是``nums[left]+nums[right]=target``那里最后忘记``left--``和``right++``，导致循环出不来。



