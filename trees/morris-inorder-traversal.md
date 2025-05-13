---
description: Tree traversal with O(1) space complexity
---

# Morris Inorder Traversal

The idea is to establish a temporary link between the current node and its in-order successor.&#x20;

When we are in a node three cases may happen:&#x20;

1. current node has no left subtree&#x20;
   * print val
   * go right
2. there is a left subtree and the right-most child of this left subtree is pointing to null
   * set the right-most child of the left subtree to point to the current node
   * move to the left child of the current node
3. there is a left subtree and the right-most child of this left subtree is already pointing to the current node
   * print the value of the current node
   * revert the temporary link
   * move to the right child of the current node



```python
def inorder_traversal(root):
    inorder = []
    curr = root
    while curr:
        if curr.left is None:
            inorder.append(curr.val)
            curr = curr.right
        else:
            prev = curr.left
            while prev.right and prev.right != curr:
                prev = prev.right
            
            # case 2
            if prev.right is None:
                prev.right = curr
                curr = curr.left
            else:
                prev.right = None
                inorder.append(curr.val)
                curr = curr.right
    return inorder
```

Time complexity: $$O(n)$$

Space complexity: $$O(1)$$
