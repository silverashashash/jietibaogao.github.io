## Two Sum-III data structure design

### Description

Design and implement a TwoSum class. It should support the following operations:`add`and`find`.

`add`- Add the number to an internal data structure.  
`find`- Find if there exists any pair of numbers which sum is equal to the value.

**Example 1:**

```
add(1); add(3); add(5);
find(4) // return true
find(7) // return false
```

只能用 hashmap

|  | Two pointers | Hashmap |
| :--- | :--- | :--- |
| $$add()$$ | $$O(n)$$ 插入操作 | $$O(1)$$ |
| $$find()$$ | $$O(n)$$ | $$O(n)$$ |

add()需要维护有序数组的话，是$$O(n)$$ 而非 $$O(logn)$$，因为出了维护这个有序数组要用到binary search之外，还有个insertion的操作，为$$O(n)$$。也不能用linked list，因为linked list没有下标访问的功能，因此无法进行binary search。所以用two pointers总有一种方法很慢。用hashmap的话add()不用排序。
- 这题表达的是不可能存在一种方法既维护了有序数组，又在很快的时间内插入

问题：add和find调用不一样多时用什么方法？
如果用hashmap把所有的two sum结果保存起来，这样find()的时间复杂敷是$$O(1)$$,但是会耗费$$O(n^2)$$的空间。适合find特别多add比较少。

* 这题要注意python里class的操作问题。 用的是`self`

```py
#自己的答案

```





