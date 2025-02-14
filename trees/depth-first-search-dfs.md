---
description: Recursive tree traversal algorithm
---

# Depth First Search (DFS)

The DFS is a traversal algorithm using backtracking. The algorithm starts at the root and explores as far as possible in each branch before backtracking, meaning you move backwards on the same path to find new nodes to traverse.&#x20;

The natural formulation is recursive:

```python
# I'll assume a binary tree with the following structure:
# def __init__(val, left = None, right = None):
#     node.val = val
#     node.left = left
#     node.right = right
def dfs(root):
    if not root:
        return 
        
    # visit the node
    
    dfs(root.left)
    dfs(root.right)
```

But it can be emulated using a stack. The idea is:

* pick a starting node and put all adjacent nodes in the stack
* pop a node, visit it and push all adjacent nodes to the stack
* repeat the process until the stack is empty

```python
def iterative_dfs(root):
    stack = [root]
    
    visited = {}
    while stack:
        node = stack[-1]
        del stack[-1]
        
        # here visit the node
        
        for adj in node.adj:
            if adj not in visited:
                stack.append(adj)
                visited.insert(adj)
```

The time complexity is $$O(|V|+|E|)$$, where $$V$$ is the set of vertices and $$E$$ is the set of edges.

The space complexity is $$O(|V|)$$, since in the worst case (which is a line of vertices where each vertex, besides the first and the last one have one incoming and one outcoming connections) we store all the vertices.



## References

* [https://www.hackerearth.com/practice/algorithms/graphs/depth-first-search/tutorial/](https://www.hackerearth.com/practice/algorithms/graphs/depth-first-search/tutorial/)
* [https://en.wikipedia.org/wiki/Depth-first\_search](https://en.wikipedia.org/wiki/Depth-first_search)
