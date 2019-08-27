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

coding style上的优化：把find two sum封装一下，然后调用``self.findtwosum()``
####思路：
- a+b=-c, 且a<=b<=c, 循环c, 在c前面找a+b, 这样可以保证unique pair
- -a=b+c, 循环a, 跳过等于a的值


错误点主要集中在去重上：
1. [0,0,0,0,0]
2. [-1,0,1,0]
3. [-2,0,1,1,2] 少一个答案
4. [-4,-2,-2,-2,0,1,2,2,2,3,3,4,4,6,6] 少很多答案，因为一个-c可能有很多种组合，就是unique pair问题。。。刚做过就忘了
5. 到后面各种错误都出来了，才意识到应该先写个2sum函数。。找出所有unique pairs







