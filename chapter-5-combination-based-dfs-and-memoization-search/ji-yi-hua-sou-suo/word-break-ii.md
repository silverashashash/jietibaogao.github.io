## Word Break II

[https://www.lintcode.com/problem/word-break-ii/](https://www.lintcode.com/problem/word-break-ii/description)

### Example

**Example 1:**

```
Input："lintcode"，["de","ding","co","code","lint"]
Output：["lint code", "lint co de"]
Explanation：
insert a space is "lint code"，insert two spaces is "lint co de".

```

**Example 2:**

```
Input："a"，[]
Output：[]
Explanation：dict is null.
```





```py
#超时的答案：
class Solution:
    """
    @param: s: A string
    @param: wordDict: A set of words.
    @return: All possible sentences.
    """
    def wordBreak(self, s, wordDict):
        # write your code here
        if not wordDict or not s:
            return []
        
        results = []
        self.helper(s, wordDict, [], results)
        
        return results
    
    def helper(self, s, wordDict, words, results):
        if len(s) == 0:
            results.append(' '.join(words) ) 
            return 
        
        for i in range(1, len(s) + 1):
            if s[:i] not in wordDict:
                continue
            words.append(s[:i])
            self.helper(s[i:], wordDict, words, results)
            words.pop()

```



