---
description: Divide-and-conquer O(n log n) sorting algorithm
---

# Merge Sort

Works by dividing an array into smaller subarrays, sorting each subarray, and then merging the sorted subarrays back together

```python
def mergesort(arr, left, right):
    if l < r:
        m = left + (right-left)//2        # equivalent to (l+r)//2, prevents overflow
        
        mergesort(arr, left, m)
        mergesort(arr, m+1, right)
        
        merge(arr, left, m, right)
```

```python
def merge(arr, left, mid, right):
    L = arr[left:mid]          # left subarray
    R = arr[mid+1:right]       # right subarray
    
    i,j,k = 0,0,left
    while i < len(L) and j < len(R):
        if L[i] <= R[j]:
            arr[k] = L[i]
            i+=1
        else:
            arr[k] = R[j]
            j+=1
        k+=1
    
    while i<len(L):
        arr[k] = L[i]
        i+=1
        k+=1
    
    while j<len(R):
        arr[k] = R[j]
        j+=1
        k+=1
        
```
