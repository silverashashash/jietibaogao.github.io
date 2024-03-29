## 3 Sum

**2Sum类问的比较多的题**

Given an array `nums` of n integers, are there elements _a, b, c_ in `nums` such that _a + b + c = 0_? Find all unique triplets in the array which gives the sum of zero.

Note:

The solution set must not contain duplicate triplets.

Example:

```
Given array nums = [-1, 0, 1, 2, -1, -4],

A solution set is:
[
  [-1, 0, 1],
  [-1, -1, 2]
]
```

统计所有和为0的三元组（Triples），要求去重

最多$$O(n^2)$$种方案，不给sort可以用hashmap

coding style上的优化：把find two sum封装一下，然后调用`self.findtwosum()`

#### 思路：

* a+b=-c, 且a&lt;=b&lt;=c, 循环c, 在c前面找a+b, 这样可以保证unique pair
* -a=b+c, 循环a, 跳过等于a的值

```py
#自己的答案
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:

        #a+b=-c
        result = []
        if not nums or len(nums) < 3:
            return result
        c_old = None
        nums.sort()


        for i in range(len(nums)-1,-1,-1):
            left, right = 0, i - 1
            if c_old == nums[i]:
                continue
            self.find_two_sum(nums, -nums[i], left, right, result)
            c_old = nums[i]
        return result


    def find_two_sum(self, nums, target, left, right, result):
        if not nums or len(nums) < 3:
            return None
        # left, right = 0, len(nums) - 1

        while left < right:
            if nums[left] + nums[right] == target:
                while left < right and nums[left] == nums[left + 1]:
                    left += 1
                while left < right and nums[right] == nums[right - 1]:
                    right -= 1

                result.append([nums[left], nums[right], -target])
                left, right = left + 1, right - 1
            elif nums[left] + nums[right] < target:
                left += 1
            else:
                right -= 1

        return result
```

错误点主要集中在去重上：a+b=-c的解法  
- ``[0,0,0,0,0]``---没去c的重，导致多了很多答案
   - 解决办法是用一个``old_c``记录每次符合条件的c，然后每次循环开始判断一下这组c是否已经计算过 
- ``[-1,0,1,0]``---  多了一个``[0,0,0]``的组合
    - 原因是当等于target时才有``left,right=0,i-1``。这表示i还没往回循环的时候right变成i-1，等于没动。应该把``left,right=0,i-1`` 放到循环开头处
- ``[-2,0,1,1,2]`` 少一个答案  
    - 原因同上，但是之前修改的时候只是加了一个right<i的判断，其实还是不对
- ``[-4,-2,-2,-2,0,1,2,2,2,3,3,4,4,6,6]`` 
    -少很多答案，因为一个c可能有很多种组合，就是unique pair问题。。。刚做过就忘了  
- 到后面各种错误都出来了，才意识到应该先写个2sum函数。。找出所有unique pairs
 - 写unique pair的时候也老出错。。等于的情况放前面还是大小于放前面要视具体题意而灵活运用

总结一下去重容易出错的地方：
- target去重
    - 我的办法是多加一个参数记录上一个target的值，实际上不需要这么做，直接在循环c的时候就可以去重，相同的跳过
- a,b组合去重-unique pairs


####九章算法思路：
力枚举三个数复杂度为$$O(N^3)$$
先考虑2Sum的做法，假设升序数列a，对于一组解ai,aj, 另一组解ak,al
必然满足`` i<k j>l ``或 ``i>k j<l``, 因此我们可以用两个指针，初始时指向数列两端
指向数之和大于目标值时，右指针向左移使得总和减小，反之左指针向右移
由此可以用 $$O(N)$$ 的复杂度解决2Sum问题，3Sum则枚举第一个数 $$O(N^2)$$

使用有序数列的好处是，在枚举和移动指针时值相等的数可以跳过，省去去重部分
```py
#九章算法答案

class Solution:
    """
    @param numbers: Give an array numbers of n integer
    @return: Find all unique triplets in the array which gives the sum of zero.
    """
    def threeSum(self, nums):
        nums.sort()
        results = []
        length = len(nums)
        for i in range(0, length - 2):
            if i and nums[i] == nums[i - 1]:
                continue
            self.find_two_sum(nums, i + 1, length - 1, -nums[i], results)
        return results

    def find_two_sum(self, nums, left, right, target, results):
        while left < right:
            if nums[left] + nums[right] == target:
                results.append([-target, nums[left], nums[right]])
                right -= 1
                left += 1
                while left < right and nums[left] == nums[left - 1]:
                    left += 1
                while left < right and nums[right] == nums[right + 1]:
                    right -= 1
            elif nums[left] + nums[right] > target:
                right -= 1
            else:
                left += 1

```


