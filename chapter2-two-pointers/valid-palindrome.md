## Valid Palindrome

valid-palindrome

* 忽略大小写和非英文字符

* 时间复杂度$$O(n)$$，虽然有两重循环，但是最多循环n次

```py
# 自己在leetcode上的答案
class Solution:
    def isPalindrome(self, s: str) -> bool:
        if s == None:
            return False

        left, right = 0, len(s) - 1

        while left < right:
            while left < right and s[left].isalnum() == False:
                left += 1
            while left < right and s[right].isalnum() == False:
                right -= 1 
            if s[left].lower() == s[right].lower():
                left += 1
                right -= 1
            else:
                return False


        return True
```

解题报告：

虽然是一道简单题，但是还是试了好多遍才成功。出的原因主要有两个：

* while内 在前两个跳过non-alnum时一开始用的是if：
  * 不能用if，因为if是一个一个移动的，当连续两个以上字符是non-alnum时，第二次指向non-alnum时会先进行字符相同的判断，造成结果错误。
* while 内的while一开始循环条件里没有left&lt;right
  * 因为满足条件会left++ 或者right--，在整个字符串都是non-isalnum时会一直往右或者往左走，造成越界
  * 最初没写这个条件是因为用的是if
* 能否把if变while？

  * 多此一举了，因为这个while根本就跟外层那个while一样。



