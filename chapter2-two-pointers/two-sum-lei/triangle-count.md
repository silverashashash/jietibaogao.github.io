## Triangle count

如果是求具体方案，理论上$$O(C^3_n)=O(n^3)$$ 。但本题是找方案总数

如果要求去重，则$$O(n^3)$$ 暴力方法

* 这道题比我想象的还费时间。原因是用two pointers的时候突然不知道该怎么去重了，一不小心就去掉正确答案了

最后看了答案：

答案1

```py
class Solution:
    """
    @param S: A list of integers
    @return: An integer
    """
    def triangleCount(self, S):
        S.sort()

        ans = 0
        for i in range(len(S)):
            left, right = 0, i - 1
            while left < right:
                if S[left] + S[right] > S[i]:
                    ans += right - left
                    right -= 1
                else:
                    left += 1
        return ans
```

答案2

```py
class Solution:
    # @param S: a list of integers
    # @return: a integer
    def triangleCount(self, S):
        edges = sorted(S, reverse=True)
        sum = 0
        for index, longest in enumerate(edges):
            i, j = index + 1, index + 2
            while j < len(edges) and edges[i] + edges[j] > longest:
                j += 1
            j -= 1
            while i < j:
                sum += j - i
                i += 1
                while i < j and edges[i] + edges[j] <= longest:
                    j -= 1
        return sum
```

自己的错误答案：

```py
class Solution:
    """
    @param S: A list of integers
    @return: An integer
    """
    def triangleCount(self, S):
        # write your code here
        if not S or len(S) < 3:
            return 0
        
        n = 0
        
        S.sort()
        # left, right = 0, len(S) - 1 
        
        for i in range(len(S)-1,-1,-1):
            left, right = 0, i - 1 
            if left < right and S[left] + S[right] > S[i]:
                n += (right - left)
                for j in range(left,right):
                    if  S[left] + S[j] > S[i]:
                        n += (j - left)
                    else:
                        left += 1 
                    
            else: #S[left] + S[right] <= S[i]
                left += 1 
            
        return n 
                 
                
```
- 当L+R>I时：
    - L往右移动的左右组合都满足：ans += r - l
    - R往左一格再会循环开头判断-->**这里卡在这里！**
- 当l+R<=I时：
    - L往右移动一格

