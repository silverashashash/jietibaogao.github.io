## Course Schedule I

[http://www.lintcode.com/problem/course-schedule/](http://www.lintcode.com/problem/course-schedule/)  
[https://leetcode.com/problems/course-schedule/](https://leetcode.com/problems/course-schedule/)

There are a total of n courses you have to take, labeled from`0`to`n-1`.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair:`[0,1]`

Given the total number of courses and a list of prerequisite **pairs**, is it possible for you to finish all courses?

**Example 1:**

```
Input: 2, [[1,0]] 

Output: true

Explanation: There are a total of 2 courses to take. 
             To take course 1 you should have finished course 0. So it is possible.
```

**Example 2:**

```
Input: 2, [[1,0],[0,1]]

Output: false

Explanation:
             There are a total of 2 courses to take. 
             To take course 1 you should have finished course 0, and to take course 0 you should
             also have finished course 1. So it is impossible.
```

**Note:**

1. The input prerequisites is a graph represented by **a list of edges**, not adjacency matrices. Read more about [how a graph is represented](https://www.khanacademy.org/computing/computer-science/algorithms/graph-representation/a/representing-graphs).
2. You may assume that there are no duplicate edges in the input prerequisites.




####思考：
1. 就是在问有没有topo？
   - 如何判断？对它进行拓扑排序，如果order不暴包括所有的点，说明有环
2. 怎么在给出edge list 的情况下做topo？

####问题：
- ``1,[]`` 这种test case应该返回true而不是false (LintCode)
- 这次``deque``初始化好像``deque([])``和``deque()``都行




```py
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        if prerequisites is None:
            return False
        
        couseNum_to_nei = {i : [] for i in range(numCourses)}
        degree = [0 for i in range(numCourses)]
        
        q = collections.deque([])
        count = 0
        
        for i, j in prerequisites:
            couseNum_to_nei[j].append(i)
            degree[i] += 1
        
        for x in range(numCourses):
            if degree[x] == 0:
                q.append(x)
        
        while q:
            node = q.popleft()
            count += 1 
            for x in couseNum_to_nei[node]:
                degree[x] -= 1
                if degree[x] == 0:
                    q.append(x)
        
        return count == numCourses

```
- 写了好几次出错的原因是几个``for``循环里总弄错for什么。






