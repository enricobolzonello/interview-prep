# Disjoint Set Union

{% hint style="info" %}
Given several elements, each of which is a separate set, a DSU will have two operations:

* combine any two sets
* find in which set an element is
{% endhint %}

The data structure does all of these operations in $$O(1)$$.

Each set will be stored as a tree, the root will be the representative of the set.&#x20;

To get $$O(1)$$ operations we need to be careful about which tree gets attached to the other one. In the naive implementation, the second tree is always attached to the first one but it can lead to trees of length $$O(n)$$.&#x20;

We can choose two heuristics to optimize this:

1. use size of the trees as rank
2. use depth of the tree

In both we attach the tree with lower rank to the one with the bigger rank.&#x20;

We will implement the first one; the second one is basically equivalent.&#x20;

```python
class DSU:
    def __init__(self, v):
        self.parent = {}
        self.size = {}
        self.parent[v] = v
        self.size[v] = 1
    
    def find_set(self, v):
        if v == parent[v]:
            return v
        return self.find_set(self.parent[v])
    
    def union_sets(self, a, b):
        a = self.find_set(a)
        b = self.find_set(b)
        if a != b:
            if self.size[a] < self.size[b]:
                a,b = b,a
            self.parent[b] = a
            self.size[a] += self.size[b]
        
```
