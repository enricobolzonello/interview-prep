---
description: simple O(n^2) sorting algorithm
---

# Insertion Sort

```python
def insertionSort(arr):
    for i in range(1, len(arr):
        key = arr[i]
        
        # move elements of arr[0,...,i-1] that are greater then key
        # to one position ahead of their current position
        j = i-1
        while j>=0 and key < arr[j]:
            arr[j+1] = arr[j]
            j -= 1
        arr[j+1] = key
```



References:

* [https://www.geeksforgeeks.org/insertion-sort/](https://www.geeksforgeeks.org/insertion-sort/)
