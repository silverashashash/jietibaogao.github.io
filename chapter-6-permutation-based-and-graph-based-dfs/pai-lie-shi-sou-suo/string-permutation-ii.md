## String Permutation II 
www.lintcode.com/problem/string-permutation-ii
跟之前的一样，注意append results用的形式（去掉）


```py
class Solution:
    """
    @param str: A string
    @return: all permutations
    """
    def stringPermutation2(self, str):
        # write your code here
        if not str:
            return [[]]
            
        results = []
        permutation = []
        visited = [False] * len(str)
        
        self.dfs(str, results, permutation, visited)
        return results
        
    def dfs(self, str, results, permutation, visited):
        if len(permutation) == len(str):
            results.append(''.join(permutation))
            # results.append(list(permutation)) 
            return 
        
        for i in range(len(str)):
            if visited[i] == True:
                continue
            if i > 0 and str[i] == str[i - 1] and visited[i - 1]:
                continue
            permutation.append(str[i])
            visited[i] = True
            self.dfs(str, results, permutation, visited)
            permutation.pop()
            visited[i] = False
            

            


```

