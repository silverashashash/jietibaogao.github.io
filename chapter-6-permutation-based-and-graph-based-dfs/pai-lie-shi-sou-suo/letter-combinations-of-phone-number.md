##  Letter Combinations of Phone Number
http://www.lintcode.com/problem/letter-combinations-of-a-phone-number/ 
http://www.jiuzhang.com/solution/letter-combinations-of-a-phone-number/
 
- 学习设置常量表




```py
#自己的答案
KEYBOARD = {
    '2': ['a', 'b', 'c'],
    '3': ['d', 'e', 'f'], 
    '4': ['g', 'h', 'i'],
    '5': ['j', 'k', 'l'],
    '6': ['m', 'n', 'o'],
    '7': ['p', 'q', 'r', 's'],
    '8': ['t', 'u', 'v'],
    '9': ['w', 'x', 'y', 'z']
}


class Solution:
    """
    @param digits: A digital string
    @return: all posible letter combinations
    """
    def letterCombinations(self, digits):
        # write your code here
        
        if not digits:
            return []
        n = len(digits)
        results = []
        self.dfs(digits, KEYBOARD, results, [], n)
        return results
        
    def dfs(self, digits, KEYBOARD, results, combination, n):
        
        if len(combination) == n:
            results.append(''.join(combination))
            return 
        
        for i in range(len(digits)):
            char_list = KEYBOARD[digits[i]]
            # print(char_list)
            
            for j in range(len(char_list)):
                # if char_list[j] in combination:
                #     continue
                combination.append(char_list[j])
                self.dfs(digits[i+1:], KEYBOARD, results, combination, n)
                combination.pop()
```



```py
#  九章答案
KEYBOARD = {
    '2': 'abc',
    '3': 'def',
    '4': 'ghi',
    '5': 'jkl',
    '6': 'mno',
    '7': 'pqrs',
    '8': 'tuv',
    '9': 'wxyz',
}

class Solution:
    """
    @param digits: A digital string
    @return: all posible letter combinations
    """
    def letterCombinations(self, digits):
        if not digits:
            return []
            
        results = []
        self.dfs(digits, 0, '', results)
        
        return results
    
    def dfs(self, digits, index, string, results):
        if index == len(digits):
            results.append(string)
            return
        
        for letter in KEYBOARD[digits[index]]:
            self.dfs(digits, index + 1, string + letter, results)

```

