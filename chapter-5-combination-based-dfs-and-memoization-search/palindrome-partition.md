## Palindrome Partition
#### 字符串切割类
http://www.lintcode.com/problem/palindrome-partitioning/
https://leetcode.com/problems/palindrome-partitioning/

python 取字符串的技巧
```py
s[:i] 取前i个字符
s[i:] 从下标i取到最后
s[::i] 字符串翻转

```


- 可以优化的地方：用dict存储已经计算过的内容：（否则可能会超时）
    - 取前后缀都会消耗 $$O(n)$$ 的时间复杂度，可以把`s`预处理，把$$n^2$$个字串`is_palindrome`的可能性计算好之后存储起来。[区间型DP]
    - 因此可以在 $$O(n^2)$$ 时间复杂度和 $$O(n^2)$$ 的空间复杂度内求出任意一个`substring`是否是回文串
- 回文串分割的整体时间复杂度是 $$O(2^n \times n)$$ 量级，因为n个字符串有`n-1`个位置可以切割，每个方案要花费`n`的时间。 因此优化是有用的。
- 一个字符串的 substring（字串） 有 $$n^2$$ 个，subsequence（子序列） 有 $$2^n$4 个