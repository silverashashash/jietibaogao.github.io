## 3 Sum

2Sum类问的比较多的题

统计所有和为0的三元组（Triples），要求去重

最多$$O(n^2)$$种方案，不给sort可以用hashmap

coding style上的优化：把find two sum封装一下，然后用self.findtwosum\(\)调



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



