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
- a+b=-c, 且a<=b<=c, 循环c, 在c前面照a+b
- -a=b+c, 循环a, 跳过等于a的值







