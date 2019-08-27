#### partition 单独定义出来

```py
# partition 单独定义出来
# https://leetcode.com/problems/sort-an-array/discuss/276916/Python-bubble-insertion-selection-quick-merge-heap-objects

class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        # self.quickSort(nums, 0, len(nums) - 1)
        # self.mergeSort(nums)
        # self.bubbleSort(nums)
        # self.insertionSort(nums)
        # self.selectionSort(nums)
        self.heapSort(nums)
        return nums

    # @quickSort
    def quickSort(self, nums, low, high):
        def partition(nums, low, high):
            i = low - 1
            pivot = nums[high]

            for j in range(low , high):
                if   nums[j] <= pivot: 
                    i = i + 1 
                    nums[i], nums[j] = nums[j], nums[i] 

            nums[i+1], nums[high] = nums[high], nums[i+1] 
            return i + 1

        if low < high:
            pi = partition(nums, low, high) 

            self.quickSort(nums, low, pi-1)
            self.quickSort(nums, pi+1, high)
```

```py
# https://leetcode.com/problems/sort-an-array/discuss/354037/Python-quicksort
class Solution:
    def sortArray(self, nums: List[int]) -> List[int]:
        self.quicksort(nums, 0, len(nums) - 1)
        return nums

    def quicksort(self, nums, lower, upper):
        if lower < upper:
            pivot = self.partition(nums, lower, upper)
            self.quicksort(nums, lower, pivot - 1)
            self.quicksort(nums, pivot + 1, upper)
        else:
            return

    def partition(self, nums, lower, upper):

        pivot = nums[upper]

        i = lower

        for j in range(lower, upper):
            if nums[j] < pivot:
                nums[i], nums[j] = nums[j], nums[i]
                i += 1

        nums[i], nums[upper] = nums[upper], nums[i]

        return i
```

```

```

```py
# https://www.jiuzhang.com/solution/sort-integers/#tag-other-lang-python
# lintcode不用返回函数
def sortIntegers(self, A):
        # write your code here
        self.quickSort(A, 0, len(A)-1)

    def quickSort(self, A, start, end):
        if start >= end:
            return

        splitpoint = self.partition(A, start, end)
        self.quickSort(A, start, splitpoint-1)
        self.quickSort(A, splitpoint+1, end)

    def partition(self, A, start, end):

        pivot = A[start]
        left, right = start+1, end

        while left <= right:
            while left <= right and A[left] <= pivot:
                left +=1
            while left <= right and A[right] >= pivot:
                right -=1

            if left <= right:
                A[left],A[right] = A[right], A[left]

        A[start], A[right] = A[right], A[start]

        return right
```

#### 

#### 

#### partition 在quicksort函数里

```py
# https://www.jiuzhang.com/solution/sort-integers/#tag-other-lang-python
class Solution:
    def sortIntegers(self, A):
        if A == None or len(A) == 0:
            return
        self.quickSort(A, 0, len(A) - 1)

    def quickSort(self, A, start, end):
        if start >= end:
            return

        left, right = start, end
        pivot = A[(start+end)//2]

        while left <= right:
            while left <= right and A[left] < pivot:
                left += 1
            while left <= right and A[right] > pivot:
                right -= 1

            if left <= right:
                A[left], A[right] = A[right], A[left]
                left += 1
                right -= 1

        self.quickSort(A, start, right)
        self.quickSort(A, left, end)
```



