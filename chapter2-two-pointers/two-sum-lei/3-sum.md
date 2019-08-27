## 3 Sum

2Sum类问的比较多的题

统计所有和为0的三元组（Triples），要求去重

最多$$O(n^2)$$种方案，不给sort可以用hashmap

coding style上的优化：把find two sum封装一下，然后用self.findtwosum\(\)调



```py
#自己的代码

```

- 调用``sort()``的时候用成``self.sort(nums)`` ``self.nums.sort()``了。``sort``是外部函数，可以直接调用。只有自己定义的函数才需要用``self``



