

merge sort code：

```py
# https://www.jiuzhang.com/solution/sort-integers/#tag-other-lang-python
class Solution:
    def sortIntegers(self, A):
        if A == None or len(A) == 0
            return
        tmp = [0]*len(A)
        self.mergeSort(A,0,len(A)-1,tmp)

    def mergeSort(self, A, start, end, tmp):
        if start >= end:
            return

        self.mergeSort(A, start, (start + end) // 2, tmp)
        self.mergeSort(A, (start + end) // 2 + 1, end)

        self.merge(A, start, end, tmp)

    def merge(self, start, end, tmp):
        mid = (start + end) // 2
        leftIndex = start
        rightIndex = mid + 1
        index = leftIndex

        while leftIndex <= mid and rightIndex <= end:
            if A[leftIndex] < A[rightIndex]:
                tmp[index] = A[leftIndex]
                leftIndex += 1
            else:
                tmp[index] = A[rightIndex]
                rightIntex += 1
            index += 1

        while leftIndex <= mid:
            tmp[index] = A[leftIndex]
            index += 1
            leftIndex += 1
        while rightIndex <= end:
            tmp[index] = A[rightIndex]
            index += 1
            rightIndex += 1
        for index in range(start, end + 1):
            A[index] = tmp[index]
```

2

```py
# https://leetcode.com/problems/sort-an-array/discuss/276916/Python-bubble-insertion-selection-quick-merge-heap-objects

def mergeSort(self, nums):
    if len(nums) > 1:
        mid = len(nums) // 2
        L = nums[:mid]
        R = nums[mid:]

        self.mergeSort(L)
        self.mergeSort(R)

        i = j = k = 0

        while i < len(L) and j < len(R):
            if L[i] < R[j]:
                nums[k] = L[i]
                i += 1
            else:
                nums[k] = R[j]
                j += 1
            k += 1

        while i < len(L):
            nums[k] = L[i]:
            i += 1
            k += 1

        while j < len(R):
            nums[k] = R[j]
            j += 1
            k += 1
```



