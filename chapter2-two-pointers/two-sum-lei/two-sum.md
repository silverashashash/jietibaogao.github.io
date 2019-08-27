## Two sum

### Description

Given an array of integers, return **indices **of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly  **one solution, and you may not use the\_same\_element twice.

```py
# 自己的code

class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        if not nums:
            return None

        hash = {}

        for i in range(len(nums)):
            if target - nums[i] in hash:
                return [hash[target - nums[i]],i]
            hash[nums[i]] = i

        return [-1,-1]
```

自己一开始是用two pointers，后来发现题目要求返回indices，所以看了答案知道要用hashmap。这题也是看了答案写出来的。需要复习。

只有返回数值而非下标的时候才能先排序再用two pointers的方法做

九章另一个答案：

```py
class Solution:
    """
    @param numbers: An array of Integer
    @param target: target = numbers[index1] + numbers[index2]
    @return: [index1 + 1, index2 + 1] (index1 < index2)
    """
    def twoSum(self, numbers, target):
        for i, a in enumerate(numbers):
            for j, b in enumerate(numbers[i + 1 - len(numbers):]):
                if a + b == target:
                    return [i, j + i + 1]
        return [-1, -1]
```

```py
enumerate(iterable, start=0)


Parameters:
Iterable:
any object that supports iteration

Start:
the index value from which the counter is 
to be started, by default it is 0
```

用二元组排序，在sort之前记录原数据的下标

```

```



