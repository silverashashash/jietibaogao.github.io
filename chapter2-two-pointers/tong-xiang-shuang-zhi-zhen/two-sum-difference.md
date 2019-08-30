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

* 程序不难写，难的是思路
* 按九章的思路，用双指针的话，先对数组进行了排序，因此需要记录原本的下标
* 因为是减法，注意绝对值的问题

```py
#我的答案（总是有错误）
class Solution:
    """
    @param nums: an array of Integer
    @param target: an integer
    @return: [index1 + 1, index2 + 1] (index1 < index2)
    """
    def twoSum7(self, nums, target):
        # write your code here
        if not nums or len(nums) < 2:
            return []

        nums = [(num, i) for i, num in enumerate(nums)]

        nums = sorted(nums, key = lambda x : x[0])
        print(nums)


        for j in range(1, len(nums)):
            i = 0
            print("i=",i)
            print("j=",j)
            while i < j:
                if abs(nums[j][0] - nums[i][0]) == abs(target):
                    if nums[i][1] < nums[j][1]:
                        return [nums[i][1] + 1, nums[j][1] + 1]
                    else:
                        return [nums[j][1] + 1, nums[i][1] + 1]
                elif abs(nums[j][0] - nums[i][0]) > abs(target):
                    i += 1
                else:
                    continue

        return []
```

* 错误1：sort 过后index会乱，要让输出的``index1<index2``
* 错误2：``[-1,0,1],target=1``的这种情况，要输出前两个而不是后两个，但是排序过后后两个是在前面的。怎么解决？
    - 答案也没解决，貌似不是错误
* 错误3: ``[-1,0,1],target=2``这种情况超时。原因是``continue``那里应该改成``break``。否则满足``else``的时候会永远困在``while``里！后面附上别人的答案仔细看。灵活运动``sorted()``函数

```py
#九章答案，用了lambda函数（匿名函数）和enumerate函数(枚举函数）
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


```py
#四种写法，如有遗落，请告知。

#twoSum7：用Hash表去重，O(N)空间，O(N)时间
#twoSum7FastSlow： 双指针法，快慢指针法，O(N)空间，O(nLogN)时间
#twoSum7LeftSteady：双指针法，左指针自变量，右指针因变量，O(N)空间，O(nLogN)时间
#twoSum7RightSteady：双指针法，右指针自变量，左指针因变量，O(N)空间，O(nLogN)时间

class Solution:
    """
    @param nums: an array of Integer
    @param target: an integer
    @return: [index1 + 1, index2 + 1] (index1 < index2)
    """
    def twoSum7(self, nums, target):
        if not nums or len(nums) < 2:
            return []
        
        hashmap = {}
        
        for j, num in enumerate(nums):
            if num - target in hashmap:
                i = hashmap[num - target]
                return sorted([i + 1, j + 1])
            elif num + target in hashmap:
                i = hashmap[num + target]
                return sorted([i + 1, j + 1])
            else:
                hashmap[num] = j 
        return []
        
    def twoSum7FastSlow(self, nums, target):
        if not nums or len(nums) < 2:
            return []
        
        numsWithIndex = [[nums[i], i] for i in range(len(nums))]
    
        if target < 0:
            target = -target
        numsWithIndex.sort()
        
        left, right = 0, 1 
        while right < len(nums):
            if left == right:
                right += 1 
            
            if numsWithIndex[right][0] - numsWithIndex[left][0] < target:
                right += 1 
            elif numsWithIndex[right][0] - numsWithIndex[left][0] > target:
                left += 1 
            else:
                return sorted([numsWithIndex[left][1] + 1, numsWithIndex[right][1] + 1])
        
        return []
            
        
    def twoSum7LeftSteady(self, nums, target):
        if not nums or len(nums) < 2:
            return []
        
        numsWithIndex = [[nums[i], i] for i in range(len(nums))]
    
        if target < 0:
            target = -target
        numsWithIndex.sort()
        
        right = 1
        for left in range(0, len(numsWithIndex) - 1):
            if left == right:
                right += 1
            while right < len(numsWithIndex) and numsWithIndex[right][0] - numsWithIndex[left][0] < target:
                right += 1 
            if left != right and right != len(numsWithIndex) and numsWithIndex[right][0] - numsWithIndex[left][0] == target:
                return sorted([numsWithIndex[right][1] + 1, numsWithIndex[left][1] + 1])
                
        return []
        
    def twoSum7RightSteady(self, nums, target):
        if not nums or len(nums) < 2:
            return []
        
        numsWithIndex = [[nums[i], i] for i in range(len(nums))]
    
        if target < 0:
            target = -target
        numsWithIndex.sort()
    
        left = 0
        for right in range(1, len(numsWithIndex)):
            while left < right and numsWithIndex[right][0] - numsWithIndex[left][0] > target:
                left += 1 
            if left != right and numsWithIndex[right][0] - numsWithIndex[left][0] == target:
                return sorted([numsWithIndex[right][1] + 1, numsWithIndex[left][1] + 1])
                
        return []
```




### python3 中用lambda函数的自定义排序

[https://blog.csdn.net/u010758410/article/details/79737498](https://blog.csdn.net/u010758410/article/details/79737498)

当待排序列表的元素由多字段构成时，我们可以通过sorted\(iterable，key，reverse\)的参数key来制定我们根据那个字段对列表元素进行排序。

`key=lambda 元素: 元素[字段索引]`

例如：想对元素第二个字段排序，则

`key=lambda y: y[1] 备注：这里y可以是任意字母，等同key=lambda x: x[1]`

看几个简单的例子。

```py
listA = [3, 6, 1, 0, 10, 8, 9]
print(sorted(listA))
listB = ['g', 'e', 't', 'b', 'a']
print(sorted(listB))
print(sorted(listB, key=lambda y: y[0]))
listC = [('e', 4), ('o', 2), ('!', 5), ('v', 3), ('l', 1)]
print(sorted(listC, key=lambda x: x[1]))
```

```py
#结果一
[0, 1, 3, 6, 8, 9, 10]
#结果二
['a', 'b', 'e', 'g', 't']
['a', 'b', 'e', 'g', 't']
#结果三
[('l', 1), ('o', 2), ('v', 3), ('e', 4), ('!', 5)]
```

### python中的枚举函数 enumerate\(\)

[http://www.runoob.com/python/python-func-enumerate.html](http://www.runoob.com/python/python-func-enumerate.html)

#### 描述

`enumerate()` 函数用于将一个可遍历的数据对象\(如列表、元组或字符串\)组合为一个索引序列，同时列出数据和数据下标，一般用在`for`循环当中。

Python 2.3. 以上版本可用，2.6 添加\`\`start\`\`\`参数。

#### 语法

以下是`enumerate()`方法的语法:

```py
enumerate(sequence, [start=0])
```

#### 参数

* sequence -- 一个序列、迭代器或其他支持迭代对象。
* start -- 下标起始位置。

  #### 返回值

  返回 enumerate\(枚举\) 对象

#### 实例

以下展示了使用`enumerate()` 方法的实例：

```py
>>>seasons = ['Spring', 'Summer', 'Fall', 'Winter']
>>>list(enumerate(seasons))
[(0, 'Spring'), (1, 'Summer'), (2, 'Fall'), (3, 'Winter')]
>>>list(enumerate(seasons, start=1))       # 下标从 1 开始
[(1, 'Spring'), (2, 'Summer'), (3, 'Fall'), (4, 'Winter')]
```

```py
#普通的 for 循环
>>>i = 0
>>> seq = ['one', 'two', 'three']
>>> for element in seq:
...     print i, seq[i]
...     i +=1
... 
0 one
1 two
2 three
```

```py
#循环使用 enumerate
>>>seq = ['one', 'two', 'three']
>>> for i, element in enumerate(seq):
...     print i, element
... 
0 one
1 two
2 three
```

本题的方法，给下标添加进list

```py
nums = [(num, i) for i, num in enumerate(nums)]
```



