---
description: Divide-and-conquer sorting algorithm
---

# Quick Sort

```
QUICKSORT(arr, low, high)
    if low<high
        pivot = PARTITION(arr, low, high)
        QUICKSORT(arr, low, pivot-1)
        QUICKSORT(arr, pivot+1, high)
```

Depending on the choice of the partition subroutine, the quicksort has different running time:

* always pick the first/last element -> $$O(n^2)$$
* choose the median -> $$T(n)\approx (c+1)n\log_2 n \in O(n\log n)$$
* randomization

## Last Element as Pivot (Lomuto's partition)

```
PARTITION(A, low, high)
    x = A[high]
    i = low-1
    for j=low to high-1
        if A[j] <= x:
            i = i+1
            A[i], A[j] = A[j], A[i]
    A[i+1], A[high] = A[high], A[i+1]
    return i+1
```

The worst-case occurs when the partitioning produces one subproblem with $$n-1$$ elements and one with 0 elements.

Assume that this partitioning arises in each recursive call:

* partitioning costs $$\Theta(n)$$ time
* recurrence: $$T(n) = T(n-1)+T(0)+\Theta(n)$$, with $$T(0)=\Theta(1)$$

which has solution $$T(n)=\Theta(n^2)$$



On average, it has time $$O(n\log n)$$

## First Element as Pivot (Hoare's partition)

In general, it is more efficient than Lomuto's parition since it does _three times fewer swaps on average_

```
PARTITION(A, low, high)
    x = A[low]
    i = low-1
    j = high+1
    
    while True
        do
            j = j-1
        while A[j] <= x
        
        do
            i = i+1
        while A[i] >= x
        
        if i<j
            A[i],A[j] = A[j],A[i]
        else
            return j
                    
```

## Randomized

```
PARTITION_random(arr, low, high)
    r = random number from low to high
    arr[r], arr[high] = arr[high], arr[r]
    return PARTITION(arr, low, high)            // Hoare's or Lovuto's 
```

