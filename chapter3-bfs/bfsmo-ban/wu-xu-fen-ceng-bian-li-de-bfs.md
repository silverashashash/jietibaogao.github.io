##无需分层遍历的BFS

```py
from collections import deque

queue = deque()
seen = set()  #等价于Java版本中的set

seen.add(start)
queue.append(start)
while len(queue):
    head = queue.popleft()
    for neighbor in head.neighbors:
        if neighbor not in seen:
            seen.add(neighbor)
            queue.append(neighbor)
```
```
start放到带扩展队列中
标记start被看过
*当队列非空：
    队首出列&被head指着
    *for head所有的邻居：
        如果这个邻居没被看过，则把它标记为看过，并放到待扩展队列里
```

上述代码中：

neighbor 表示从某个点 head 出发，可以走到的下一层的节点。
set/seen 存储已经访问过的节点（已经丢到 queue 里去过的节点）
queue 存储等待被拓展到下一层的节点
set/seen 与 queue 是一对好基友，无时无刻都一起出现，往 queue 里新增一个节点，就要同时丢到 set 里。