---
description: Level tree traversal
---

# Breadth First Search (BFS)

In BFS you visit the tree layer by layer, exploring the neighbour nodes before proceeding to the next level.&#x20;

```python
def dfs(root):
    q = deque()
    q.append(root)
    
    visited = {}
    visited.insert(root)
    
    while q:
        node = q.popleft()
        
        for adj in node.adj:
            if adj not in visited:
                q.append(adj)
                visited.insert(adj)
```

The complexity is the same as DFS, $$O(|V|+|E|)$$.

A nice property is that the discovery edges of BFS form a spanning tree (graph that contains all vertices and a subset of edges that allows to connect each vertex with one and only one path).

While DFS can be used to determine the shortest path, BFS cannot.&#x20;



## References

* [https://www.dei.unipd.it/\~depoli/fi2ae/slides\_pw/old-lucidi-06/grafi/G5\_BFS.pdf](https://www.dei.unipd.it/~depoli/fi2ae/slides_pw/old-lucidi-06/grafi/G5_BFS.pdf)
* [https://www.hackerearth.com/practice/algorithms/graphs/breadth-first-search/tutorial/](https://www.hackerearth.com/practice/algorithms/graphs/breadth-first-search/tutorial/)
