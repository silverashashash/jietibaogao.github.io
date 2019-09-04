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
*当队列非空：
    队首出列&被head指着
    *for head所有的邻居：
        如果这个邻居没被看过，则把它标记为看过，并放到待扩展队列里
```