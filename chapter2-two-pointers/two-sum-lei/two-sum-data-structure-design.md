## Two Sum-III data structure design

### Description

Design and implement a TwoSum class. It should support the following operations:`add`and`find`.

`add`- Add the number to an internal data structure.  
`find`- Find if there exists any pair of numbers which sum is equal to the value.

只能用 hashmap

|  | Two pointers | Hashmap |
| :--- | :--- | :--- |
| add\(\) | O\(n\) 插入操作 | O\(1\) |
| find\(\) | O\(n\) | O\(n\) |

add\(\)  是O\(n\) 而非 O\(logn\)，因为出了维护这个有序数组要用到binary search之外，还有个insertion的操作，为O\(n\)。不能用linked list，因为linked list没有下标，因此无法进行binary search

问题：add和find操作不一样多时用什么方法？

