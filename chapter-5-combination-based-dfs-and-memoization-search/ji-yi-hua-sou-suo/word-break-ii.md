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

```py
#看了答案之后的解答
class Solution:
    """
    @param: s: A string
    @param: wordDict: A set of words.
    @return: All possible sentences.
    """
    def wordBreak(self, s, wordDict):
        # write your code here
        if s is None or wordDict is None:
            return []

        return self.helper(s, wordDict, {})

    def helper(self, s, wordDict, memo):
        if len(s) == 0:
            return []

        results = []

        if s in memo:
            return memo[s]

        if s in wordDict:
            results.append(s)

        for i in range(1, len(s) + 1):
            if s[:i]  not in wordDict:
                continue

            segments = self.helper(s[i:], wordDict, memo)

            for sg in segments:
                results.append(s[:i] + ' ' + sg)

        memo[s] = results

        return results
```

* 这个答案必须要额外处理：
  ```
    # if s in wordDict:
    #     partitions.append(s)
  ```

```py
#另一种不需要额外处理的答案
class Solution:
    def wordBreak(self, s: str, wordDict: List[str]) -> List[str]:
        return self.helper(s, wordDict, {})
    
    def helper(self, s, wordDict, memo):
        if not s:
            return [""]
        if s in memo:
            return memo[s]
        
        results = []
        
        for i in range(1, len(s) + 1):
            if s[:i] not in wordDict:
                continue 
            
            segments = self.helper(s[i:], wordDict, memo)
            
            for sg in segments:
                if sg:
                    results.append(s[:i] + ' ' + sg)
                else:
                    results.append(s)
            
        memo[s] = results
        
        return results
        
```

* 对比一下就明白为什么需要做那个额外处理



