## Two sum data structure design

只能用 hashmap

|  | Two pointers | Hashmap |
| :--- | :--- | :--- |
| add\(\) | O\(n\) 插入操作 | O\(1\) |
| find\(\) | O\(n\) | O\(n\) |

add\(\)  是O\(n\) 而非 O\(logn\)，因为出了维护这个有序数组要用到binary search之外，还有个insertion的操作，为O\(n\)。不能用linked list，因为linked list没有下标，因此无法进行binary search

问题：add和find操作不一样多时用什么方法？



