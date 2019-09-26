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
- 考虑下面的图


```
      C----F
    / |    | \
A -B  |    |  G
    \ |    | /
      D----E

```
- A-B-C-D一定不会是最短路径，原因是C和D在同一层。因此可以哟过BFS先做一遍搜索。
- 但是有的路径走不到destination，比如下图A-J的路径，走到B点是肯定不会走到J的。走到B点就要浪费很多时间返回。解决办法是从end 到start做搜索。


```
          A
         /  \
        B    C
      /  \  / \
     D   E G   H
      \ /   \ /
       F     I
            /
           J

```
####最终的方案：
- 从end到start做一次BFS，并且吧距离end的距离都保存在distance中。（保存节点的层号）
- 然后再从start到end做一次DFS，每一步必须确保离end的distance越来越近
- 这里寻找下一个变换单词的方法是建立index，即，如果有一个单词abc，分别去掉第1，2，3个字符之后，把abc这个单词分别扔进%bc，a%c，ab%这三个不同的key的hash里，hash里的key是去掉一个字符之后的pattern，value是一个set，保存满足这个pattern的所有单词。

####最坏情况
- 完全图（所有node都有连边）是$$O(n!)$$





















