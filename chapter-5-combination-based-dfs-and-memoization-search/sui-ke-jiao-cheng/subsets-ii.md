## subsets II 要求去重

####解法：
在for循环里加上

```py
if i != 0 and nums[i] == nums[i - 1] and i != start_index: 
# i!= 0: 防止数组越界
# i > start_index 去重
    continue

```

- 去重一定发生在搜索的过程中

- 即使用hashset去重，list is un-hashble , 可以用seriazilation， 变成一个字符串再hash