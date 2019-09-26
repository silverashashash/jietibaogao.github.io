## Word Pattern II 
http://www.lintcode.com/problem/word-pattern-ii/
- 做法和 Wildcard Match / Regular Expression Match 类似

- 除了往下传递字符串，还要传递一一映射关系（映射表 mapping），因为一个字母只能匹配一个单词，不能同时对应多个字符串。
- 没法向regular expression match那样记忆化，因为一共4个参数，用memo存起来太麻烦（mapping是个哈希表，基本不会拿来做key），优化效果不是很好。记忆化的话有重复的效果好，这个题没啥重复
    - 有一道题是拿哈希表做key，leetcode: shortest path visiting all nodes (https://leetcode.com/problems/shortest-path-visiting-all-nodes/)。这遍历所有点的最短路径，点可以多次访问.
        - 需要把经过哪些点作为一个key存在哈希表里。不能用set作为key，因为set存的是内存地址，因此调用的时候比较的是内存地址而不是值。应该变成binary，作为一个只有0和1的整数存在哈希表的key里。比如1234中，1和3访问过，key就是1010。这种方法叫做状态压缩（state compression或者binary compression）。20的范围以内都可以用状态压缩。在$$2^n \times n$$的范围内进行BFS
        - 注意状态压缩和bit array不是一回事

- 之前学过求所有路径用DFS，求最短路径用BFS。本题求的是所有最短路径，因此用BFS+DFS
- 如果只用DFS求所有路径，并不断更新最短路径，需要$$O(n!)$$