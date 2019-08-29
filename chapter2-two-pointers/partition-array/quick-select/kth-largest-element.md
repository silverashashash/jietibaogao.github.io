## kth largest element



- 注意这题是降序排列




```py
#自己的做法 (看了讲解以后）
class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        # corner case here
        # recursion 
        # return the k-th largest number 
        
        if not nums:
            return None
        
        start, end = 0, len(nums) - 1
        
        return self.quick_select(nums, start, end, k)
        
        
    def quick_select(self, nums, start, end, k):
        # corner
        
        left, right = start, end
        mid = (start + end) // 2
        pivot = nums[mid]
        
        while left <=  right:
            while left <= right and nums[left] > pivot:
                left += 1
            while left <= right and nums[right] < pivot:
                right -= 1
            if left <= right:
                nums[left], nums[right] = nums[right], nums[left]
                left, right = left + 1, right - 1
                
        if start + k - 1 <= right:
            return self.quick_select(nums, start, right, k)
        if start + k - 1 >= left:
            return self.quick_select(nums, left, end, k - (left - start))
        
        return nums[right + 1]    
```

注意的地方：
- ``start``, ``end``是``nums``的绝对坐标，``k``是传入函数里的那段sublist的相对第``k``大个数。这么做时因为讨论的时候比较简单。