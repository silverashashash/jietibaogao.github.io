## subsets II 要求去重

####解法：
在for循环里加上


```py
            if i != 0 and nums[i] == nums[i - 1] and i != start_index:
                continue
```

