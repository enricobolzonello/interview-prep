---
description: >-
  SSSP for weighted, undirected and connected graphj without any negative weight
  cycle
---

# Dijkstra's Algorithm

The approach is to keep a priority queue with pairs of the type $$(\text{dist},\text{node})$$ where $$dist$$ is the current value of the shortest distance from the source to $$node$$. Also keep an additional array/matrix to store the shortest distances to all nodes from the source node.

The algorithm continues until the heap is empty, at each step doing the following:

* pop from the heap, this will return the nearest node from source not yet processed
* look out for the adjacent nodes, if the  current reachable distance is better than the previous distance is better than the previous distance, we update the distance and push it into the queue.



```python
# assume that the vertices go from 0 to n-1
def dijkstra(source, graph, n):
    min_heap = []
    heappush(min_heap, (0,source))
    
    dist_to = [float('inf')] * n
    dist_to[source] = 0
    
    while min_heap:
        dist, node = min_heap.pop()
        
        for adj, weight in graph[node]:
            if dist+weight < dist_to[adj]:
                dist_to[adj] = dist+weight
                heappush(min_heap, (dist+weight, adj))
    return dist_to
```

Time complexity: $$O(E\log V)$$

Space complexity: $$O(|V|+|E|)$$
