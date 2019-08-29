## Two sum difference

见随课教程

### Description

Given an array of integers, find two numbers that their difference equals to a target value.  
where index1 must be less than index2. Please note that your returned answers \(both index1 and index2\) are NOT zero-based.

### Example

Example 1:

```
Input: nums = [2, 7, 15, 24], target = 5 
Output: [1, 2] 
Explanation:
(7 - 2 = 5)

```

Example 2:

```
Input: nums = [1, 1], target = 0
Output: [1, 2] 
Explanation:
(1 - 1 = 0)
```



- 程序不难写，难的是思路
- 按九章的思路，用双指针的话，先对数组进行了排序，因此需要记录原本的下标
- 因为是减法，注意绝对值的问题



```py
#九章答案，用了lambda函数（匿名函数）
class Solution:
    """
    @param nums {int[]} n array of Integer
    @param target {int} an integer
    @return {int[]} [index1 + 1, index2 + 1] (index1 < index2)
    """
    def twoSum7(self, nums, target):
        # Write your code here
        nums = [(num, i) for i, num in enumerate(nums)]
        target = abs(target)    
        n, indexs = len(nums), []
    
        nums = sorted(nums, key=lambda x: x[0])

        j = 0
        for i in range(n):
            if i == j:
                j += 1
            while j < n and nums[j][0] - nums[i][0] < target:
                j += 1
            if j < n and nums[j][0] - nums[i][0] == target:
                indexs = [nums[i][1] + 1, nums[j][1] + 1]

        if indexs[0] > indexs[1]:
            indexs[0], indexs[1] = indexs[1], indexs[0]

        return indexs

```

###python3 中用lambda函数的自定义排序

https://blog.csdn.net/u010758410/article/details/79737498

