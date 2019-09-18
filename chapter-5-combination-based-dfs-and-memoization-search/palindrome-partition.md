## Palindrome Partition
#### 字符串切割类
http://www.lintcode.com/problem/palindrome-partitioning/
https://leetcode.com/problems/palindrome-partitioning/
要求切割后每个substring都是回文串

python 取字符串的技巧
```py
s[:i] 取前i个字符
s[i:] 从下标i取到最后
s[::-1] 字符串翻转

```


- 可以优化的地方：用dict存储已经计算过的内容：(判断是否是回文串不可能在O(1)时间内完成)
    - 取前后缀都会消耗 $$O(n)$$ 的时间复杂度，可以把`s`预处理，把$$n^2$$个字串`is_palindrome`的可能性计算好之后存储起来。[区间型DP]
    - 因此可以在 $$O(n^2)$$ 时间复杂度和 $$O(n^2)$$ 的空间复杂度内求出任意一个`substring`是否是回文串
- 回文串分割的整体时间复杂度是 $$O(2^n \times n)$$ 量级，因为n个字符串有`n-1`个位置可以切割，每个方案要花费`n`的时间。 因此优化是有用的。
- 一个字符串的 substring（字串） 有 $$n^2$$ 个，subsequence（子序列） 有 $$2^n$4 个



```py
#没用记忆化搜索，自己的答案
class Solution:
    """
    @param: s: A string
    @return: A list of lists of string
    """
    def partition(self, s):
        # write your code here
        if s is None:
            return []
        if len(s) == 0:
            return [[]]
        path = []
        results = []
        self.helper(s, path, results)
        return results
    
    def helper(self, s, path, results):
        if s == "":
            results.append(list(path))
        for i in range(len(s)):
   #         if len(s) < i + 1:
   #             break
            if self.is_palindrome(s[:i + 1]): 
                path.append(s[:i + 1]) 
                self.helper(s[i + 1:], path, results)
                path.pop()
    
    def is_palindrome(self, s):
        return s == s[::-1]      

```



