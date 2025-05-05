---
description: Find an order of the vertices
---

# Topological Sorting

{% hint style="info" %}
A topological sort of a DAG $$G$$ is a linear ordering of all its vertices such that if $$G$$ contains an edge $$(u,v)$$ then $$u$$ appears before $$v$$ in the ordering
{% endhint %}

Can be defined only if the graph is a DAG (Directed Acyclical Graph).



```python
def topological_sort(graph, n):
    # suppose graph is represented as an adjacency list with default dict
    visited = [False] * n
    res = []
    
    def dfs(node):
        visited[node] = True
        for nei in graph[node]:
            if not visited[nei]:
                dfs(nei)
        res.append(v)
    
    for i in range(n):
        if not visited[i]:
            dfs(i)
            
    return ans[::-1]
```
