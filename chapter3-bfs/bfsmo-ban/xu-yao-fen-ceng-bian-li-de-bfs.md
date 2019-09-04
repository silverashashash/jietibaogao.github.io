##需要分层遍历的BFS
```py
from collections import deque

queue = deque()
seen = set()

seen.add(start)
queue.append(start)
while len(queue):
    size = len(queue)
    for _ in range(size):
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
    *for 「当前」队列的长度：
        队首出列&被head指着：
        *for head所有的邻居：
            如果这个邻居没被看过，则把它标记为看过，并放到待扩展队列里
                    

    
    
```