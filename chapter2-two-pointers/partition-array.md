## Partition Array

partition 是 in place的，in place = no extra space = constant space

### partition 模版

![](/assets/Screen Shot 2019-08-22 at 3.13.53 PM.png)

左右两边分别找到相应的数并交换

* 结束条件写成 `left <= right`, 表示结束后左右相邻并错开
  `[O|O|O|O|R|L|O|O|O|O]` 或者 `[O|O|O|O|R|O|L|O|O|O]`
* `left < right` 可能会停在同一个位置结束，但是这个位置属于左边还是右边并不知道，必须通过多加一个if判断。

这个代码用到quicksort的问题是要quicksort把等于pivot的情况单独拿出来讨论，是为了避免在数组元素一样时，退化成$$O(n^2)$$

* quicksort, `A[i] == pivot`时哪都不属于  
  ![](/assets/Screen Shot 2019-08-22 at 3.33.31 PM.png)

* partition，`A[i]==pivot`时属于右侧  
  ![](/assets/Screen Shot 2019-08-22 at 3.34.51 PM.png)

### Description

Given an array`nums`of integers and an int`k`, partition the array \(i.e move the elements in "nums"\) such that:

* All elements ``<k`` are moved to the _left_
* All elements ``>=k ``are moved to the _right_

Return the partitioning index, i.e. the first index i ``nums[i] >=k``.

####Notice
You should do really partition in array nums instead of just counting the numbers of integers smaller than k.

If all elements in nums are smaller than k, then return nums.length



```py
# 自己的答案
class Solution:
    """
    @param nums: The integer array you should partition
    @param k: An integer
    @return: The index after partition
    """
    def partitionArray(self, nums, k):
        # write your code here
        
        # pivot = k 
        if not nums:
            return 0
        
        left, right = 0, len(nums) - 1 
        nums.sort()
        
        if nums[len(nums) - 1 ] < k:
            return len(nums)
        if nums[0] > k:
            return 0
        
        while left <= right:
            while left <= right and nums[left] < k:
                left += 1 
            while left <= right and nums[right] >= k:
                right -= 1 
                
            if left <= right:
                nums[left], nums[right] = nums[right], nums[left]
                left, right = left + 1, right - 1
            
        return left
```

- 错误点1: partition做起来很简单，但是循环出来判断返回值的时候一直出错，直到我看到Notice里写的**If all elements in nums are smaller than k, then return nums.length**...
- 错误点2: 另一个错误的地方是，partition的``A[i] == pivot``的情况是属于右侧的，而quicksort是谁都不属于。如果没注意到这点写成quicksort的形式，就会导致出现``A[i]==pivot``时if特别复杂
- 另外注意partition并不是排序哦


```py
#九章的答案
class Solution:
    """
    @param nums: The integer array you should partition
    @param k: As description
    @return: The index after partition
    """
    def partitionArray(self, nums, k):
        start, end = 0, len(nums) - 1
        while start <= end:
            while start <= end and nums[start] < k:
                start += 1
            while start <= end and nums[end] >= k:
                end -= 1
            if start <= end:
                nums[start], nums[end] = nums[end], nums[start]
                start += 1
                end -= 1
        return start
```

- 老师的答案这样就不用关心``pivot``是否全部大于或者小于数组元素的情况了。主要原因是``start<=end``这里，当所有元素都大于或小于``pivot``时，结束前两个指针会指向同一个位置。此时满足内部while的条件，因此还会再移动一次。



