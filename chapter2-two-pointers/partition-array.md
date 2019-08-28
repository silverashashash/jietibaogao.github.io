## Partition Array

partition 是 in place的，in place = no extra space = constant space

### partition 模版

![](/assets/Screen Shot 2019-08-22 at 3.13.53 PM.png)

左右两边分别找到相应的数并交换

* 结束条件写成 `left <= right`, 表示结束后左右相邻并错开
  `[O|O|O|O|R|L|O|O|O|O|]`
* `left < right` 可能会停在同一个位置结束，但是这个位置属于左边还是右边并不知道，必须通过多加一个if判断。

这个代码用到quicksort的问题是要quicksort把等于pivot的情况单独拿出来讨论，是为了避免在数组元素一样时，退化成$$O(n^2)$$

* quicksort, `A[i] == pivot`时哪都不属于  
  ![](/assets/Screen Shot 2019-08-22 at 3.33.31 PM.png)

* partition，`A[i]==pivot`时属于右侧  
  ![](/assets/Screen Shot 2019-08-22 at 3.34.51 PM.png)

### Description

Given an array`nums`of integers and an int`k`, partition the array \(i.e move the elements in "nums"\) such that:

* All elements &lt;_k _are moved to the _left_
* All elements &gt;=_k _are moved to the _right_

Return the partitioning index, i.e the first index i nums[i] >=k.

