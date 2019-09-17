## 可以拓展到排列类搜索的递归方式 （permutation）




```py
class Solution:
    """
    @param nums: A set of numbers
    @return: A list of lists
    """
    def subsets(self, nums):
        # write your code here
        subset = []
        results = []
        if nums is None:
            return []
        if nums == []:
            return [[]]
        
        nums = sorted(nums)
        self.dfs(nums, 0, subset, results)
        
        return results
    
    def dfs(self, nums, start_index, subset, results):
        results.append(list(subset))
        for i in range(start_index, len(nums)):
            subset.append(nums[i])
            self.dfs(nums, i + 1, subset, results)
            subset.pop()
```

- python还可以用一行代码解决for循环里的内容：


```py
for i in range(start_index, len(nums)):
    self.dfs(nums, i + 1, subset + [num[i]], results

```
这样还不用pop()，因为subset的值并没有改变，而是产生了一个新的subset往下传递



####九章答案里有个四种解法的

提供4种python做法：

1. 使用DFS组合的思路，对于每一位，考虑是否使用，是append再DFS，否pop再DFS
2. 使用DFS排列的思路，对于每一位，从这一位往后进行DFS，DFS结束后要pop（回溯）
3. 使用BFS排列的思路，queue种的每一次subset再向后进行选择，但是因为没有记录index，所以用 subset[-1] < nums[i]来找index
4. 使用BFS组合的思路，借助位运算，来标记每一位是否被使用
总结：
- DFS是需要回溯的
- python的deep copy 如果是一重list 可用用[:] 来进行，再多就不行了- 
- 排列类算法可以继续用在subsets II 中

```py
class Solution:
    """
    @param nums: A set of numbers
    @return: A list of lists
    """
    def subsets(self, nums):
        # write your code here
        if nums==None:
            return []
        if len(nums) == 0:
            return [[]]
        res = []
        subset = []
        nums.sort()
        self.helper4(res,nums)
        return res
        
    def helper1(self,subset,res,index,nums):
        if index == len(nums):
            res.append(subset[:])
            return
        subset.append(nums[index])
        self.helper1(subset,res,index+1,nums)
        subset.pop(-1)
        self.helper1(subset,res,index+1,nums)
        
    def helper2(self,subset,res,index,nums):
        res.append(subset[:])
        for i in range(index,len(nums)):
            subset.append(nums[i])
            self.helper2(subset,res,i+1,nums)
            subset.pop(-1)
        
    def helper3(self,res,nums):
        q = []
        q.append([])
        while q:
            subset = q.pop()[:]
            res.append(subset)
            for i in range(len(nums)):
                if not subset or subset[-1] < nums[i]:
                    newSubset = subset[:]
                    newSubset.append(nums[i])
                    q.append(newSubset)
        return res
        
    def helper4(self,res,nums):
        n = len(nums)
        for i in range(1<<n):
            subset = []
            for j in range(n):
                if i & 1 << j:
                    subset.append(nums[j])
            res.append(subset)
        return res

```

