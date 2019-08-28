## Remove duplicate numbers in array

#### Description

Given an array of integers, how many three numbers can be found in the array, so that we can build an triangle whose three edges length is the three numbers that we find?  


### Example

**Example 1:**

```
Input: [3, 4, 6, 7]
Output: 3
Explanation:
They are (3, 4, 6), 
         (3, 6, 7),
         (4, 6, 7)

```

**Example 2:**

```
Input: [4, 4, 4, 4]
Output: 4
Explanation:
Any three numbers can form a triangle. 
So the answer is C(3, 4) = 4
```


思路：for 循环一个 c，再找出几个a+b&gt;c
如果要求列出具体方案，理论上$$O(C_n^3)=O(n^3)$$
如果要求去重，则需要$$O(n^3)$$暴力枚举法




```py
#自己的做法

```

- 这道题不一样的地方在于可以有重复的元素，这反而比想象的难了，因为