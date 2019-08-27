## Quick Sort

* 每次往下递归**之前**要做的一件事是partition。
* 往下递归的input是一个partition后整体有序的数组，其中左半边的数组范围是\[:pivot\_\_index-1\], 右半边数组范围是\[pivot\_\_index+1\]
* 递归到最底层再回来的时候每次返回的是一个sorted list。一直往出口走就行了。
* 所以quicksort要先partition，再递归

P39

The quick sort algorithm for sorting arrays proceeds recursively - it selects an elements \(the "pivot"\), reorders the arrays to make all the elements **less than or equal** to the pivot appear first, followed by all the elements greater than the pivot. The two subarrays are then sorted recursively.

Implemented naively, quick sort has large run times and deep function call stacks on arrays with many duplicates because the subarrays may differ greatly in size. One solution is to reorder the array so that all elements less than the pivot appear first, followed by elements equals to the pivot, followed by elements greater than the pivot. This is known as Dutch national flag partitioning, because the Dutch national flag consists of three horizontal bands, each in a different color.

Q: Dutch national flag problem:

\[ quick sort 的 partition \]

Write a program that takes an array A and an index i into A, and rearrange the elements such that all elements less than A\[i\] \(the "pivot"\) appear first, followed by elements equal to the pivot, followed by elements greater than the pivot.

A: We can avoid using O\(n\) additional space at the cost of increased time complexity as follows. In the first stage, we iterate through A starting from index 0, then index 1, etc. In each iteration, we seek an element smaller than the pivot - as soon as we find it, we move it to the subarray of smaller elements via an exchange. This moves all the elements less than the pivot to the start of the array. The second stage is similar to the first one, the difference being that we move elements greater than the pivot to the end of the array.

```py
RED, WHITE, BLUE = range(3)

def dutch_flag_partition(pivot_index, A):
    pivot = A[pivot_index]
    #First pass: group elements smaller than pivot:
    for i in range(len(A)):
        #look for a smaller element.
        for j in range(i + 1, len(A)):
            if A[j] < pivot:
                A[i], A[j] = A[j], A[i]
                break
    #Second pass: group elements larger than pivot
    for i in reversed(range(len(A))):
        if A[i] < pivot:
            break
        # Look for a larger element. Stop when we reach an element less than
        # pivot, since first pass has moved them to the start of A.
        for j in reversed(range(i)):
            if A[j] > pivot:
                A[i], A[j] = A[j], A[i]
                break
```

The additional space complexity is now $$O(1)$$, but the time complexity is $$O(n^2)$$, e.g, if i = n/2 and all elements before i are greater than A\[i\], and all elements after i are less than A\[i\]. Intuitively, this approach has bad time complexity because in the first pass when searching for each additional element smaller than the pivot we start from the beginning. However, there is no reason to start from so far back - we can begin from the last location we advanced to. \(Similar comments hold for the second pass.\)

To improve time complexity, we make a single pass and move all the elements less than the pivot to the beginning. In the second pass we move the larger elements to the end. It is easy to perform each pass in a single iteration, moving out-of-place elements as soon as they are discovered.

```py
RED, WHITE, BLUE = range(3)

def dutch_flag_partition(pivot_index, A):
    pivot = A[pivot_index]
    # First pass: group elements smaller than pivot.
    smaller = 0
    for i in range(len(A)):
        if A[i] < pivot:
            A[i], A[smaller] = A[smaller], A[i]
            smaller += 1
    # Second pass: group elements larger than pivot
    larger = len(A) - 1
    for i in reversed(range(len(A))):
        if A[i] < pivot:
            break
        elif A[i] > pivot:
            A[i], A[larger] = A[larger], A[i]
            larger += 1
```

The time complexity is O\(n\) and the space complexity is O\(1\).

The algorithm we now present is similar to the one sketched above. The main difference is that it performs classification into elements less than, equal to, and greater than the pivot in a single pass. This reduces runtime, at the cost of a trickier implementation. We do this by maintaining four subarrays: bottom \(elements less than pivot\), middle \(elements equals to pivot\), unclassified, and top in unclassified, and move elements into one of bottom, middle, and top groups according to the relative order between the incoming and unclassified element and the pivot.

```py
RED, WHITE, BLUE = range(3)

def dutch_flag_partition(pivot_index, A):
    pivot = A[pivot_index]
    # Keep the following invariants during partitioning:
    # bottom group: A[:smaller].
    # middle group: A[smaller:equal].
    # unclassified group: A[equal:larger].
    # top group: A[larger].
    smaller, equal, larger = 0, 0, len(A)
    # Keep iterating as long as there is an unclassified element
    while equal < larger:
        # A[equal] is the incoming unclassified element. 
        if A[equal] < pivot:
            A[smaller], A[equal] = A[equal], A[smaller]
            smaller, equal = smaller + 1, equal + 1
        elif A[equal] == pivot:
            equal += 1
        else:  # A[equal] > pivot
            larger -= 1
            A[equal], A[larger] = A[larger], A[equal]
```



