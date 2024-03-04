---
description: In-place comparison O(n^2) sorting algorithm
---

# Selection Sort

```python
def selectionsort(arr):
    for i in range(len(arr)):
        min_idx = i
        for j in range(i+1, len(arr)):
            if arr[min_idx] > arr[j]:
                min_idx = j
        A[i], A[min_idx] = A[min_idx], A[i]
```
