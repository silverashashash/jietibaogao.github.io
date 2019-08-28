## Valid Palindrome II

### Description

Given a non-empty string`s`, you may delete at most one character. Judge whether you can make it a palindrome.

1. The string will only contain lowercase characters.
2. The maximum length of the string is 50000.

可以 删掉一个字符

* 贪心法（证明没看懂）
  * 贪心的证明是如果遇到的第一个不相同的字符组，删掉其中一个能变成palindrome，则原题成立。

解题报告：

* 出错点1: 只能删掉一个字符。一开始写的程序是while里会不停删掉，直到变成palindrome为止
  * 自己的解决办法是加了一个参数n，记录跳过的次数
* 出错点2: 出现一种情况："cupuaupucu" 删掉最左边那个和最右边那个都能满足删掉后指向的两个字符相同，但是只有删掉右边那个才满足题意。一开始写的程序是执行删掉左边的操作，这导致了结果是false 。
  * 自己的解决办法是写了一个isPalindrome的函数判断首尾数组是否是回文。
* 出错点3: "acba" 这种情况也报错了，原因是第一步判断s\[l\]==s\[r\]的时候写成isPalindrome\(s,left,right\)了
* 出错点4: 一开始把right=len\(s\)-1 写成right=len\(s\)了导致数组越界

```py
# 自己的答案，貌似时间太长了
class Solution:
    def validPalindrome(self, s: str) -> bool:
        if s == None:
            return False

        left, right = 0, len(s)-1
        n = 0

        while left < right:
            # print(left,right)
            if s[left] == s[right]:
                left += 1
                right -= 1
            else:
                if self.isPalindrome(s, left + 1, right):
                    left += 1
                elif self.isPalindrome(s, left, right - 1):
                    right -= 1
                else:
                    return False
                n += 1

            if n > 1:
                return False

        return True    


    def isPalindrome(self, s, start, end):
        while start < end:
            if s[start] == s[end]:
                start += 1
                end -= 1
            else:
                return False
        return True
```

九章答案：\(很棒\)

```py
# 老师的答案
  class Solution:
    """
    @param s: a string
    @return: nothing
    """
    def validPalindrome(self, s):
        left, right = self.two_pointer(s, 0, len(s) - 1)            
        if left >= right:
            return True

        return self.is_palindrome(s, left + 1, right) or self.is_palindrome(s, left, right - 1)

    def is_palindrome(self, s, left, right):
        left, right = self.two_pointer(s, left, right)
        return left >= right

    def two_pointer(self, s, left, right):
        while left < right:
            if s[left] != s[right]:
                return left, right
            left += 1
            right -= 1
        return left, right
```

* two\_pointer\(\): 遇到左右不同时返回左右下标
* is\_palindrome\(\): s\[left:right\] 是否是palindrome
* 利用了python可以同时返回两个值的特性
* 另外要注意，**如果一个字符是回文串，那么while结束后要么left==right（奇数个字符），要么left&gt;right（偶数个字符）。**这是two\_pointer的运行结果之一。

学生的答案：

```py

```



