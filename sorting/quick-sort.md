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



The goal is to analyze the **expected** number of comparisons.

Let S be a set of numbers. For $$1\le i\le n$$, let $$S_{(i)}$$denote the element of rank i (ith smallest element).

Define $$X_{ij}=\begin{cases} 1&\text{if }S_{(i)}, S_{(j)}\text{ are compared}\\ 0&\text{otherwise} \end{cases}$$

So the total number of comparisons is $$\sum_{i=1}^n\sum_{j>i}X_{ij}$$. We are interested in the expected number of comparison which is:&#x20;

$$
E\Bigg[\sum_{i=1}^{n}\sum_{j>i}X_{ij}\Bigg]=\sum_{i=1}^n\sum_{j>i}E[X_{ij}]
$$

by linearity of expectation.

Let $$p_{ij}$$be the probability that $$X_{ij}=1$$. Since $$X_{ij}$$ only assumes values 0 and 1, $$E[X_{ij}]=p_{ij}*1+(1-p_{ij})*0=p_{ij}$$



To determine the probability, we can view the execution of the algorithm as a binary tree $$T$$. The root is labeled with the element $$r$$chosen, the left sub-tree contains the elements in $$S_1$$and the right subtree contrains the elements in $$S_2$$.

There is a comparison between $$S_{(i)}$$ and $$S_{(j)}$$ if and only if one of these element is an ancestor of the other.

&#x20;For the analysis, we are interested in the **level-order traversal** $$\pi$$ of the nodes. Observe two things:

*   there is a comparison between $$S_{(i)}$$ and $$S_{(j)}$$ if and only if $$S_{(i)}$$

    or $$S_{(j)}$$ occurs earlier in the permutation $$\pi$$ than any element $$S_{(l)}$$ such that $$i<l<j$$
* any  of the elements $$S_{(i)} , S_{(i+1)},...,S_{(j)}$$ is equally likely to be the first of these elements to be chosen as a partitioning element. Thus $$p_{ij}=\frac{2}{j-i-1}$$

Finally the expected number of comparisons is:&#x20;

$$
\begin{align*}
\sum_{i=1}^n\sum_{j>i}p_{ij} &=\sum_{i=1}^n\sum_{j>i} \frac{2}{j-i+1}\\
&\le \sum_{i=1}^n\sum_{k=1}^{n-i+1}\frac{2}{k}\\
&\le 2\sum_{i=1}^n\sum_{k=1}^n\frac{1}{k}
\end{align*}
$$

It follows that the expected number of comparisons is bounded above by $$2nH_n$$, where $$H_n$$ is the Harmonic number



**References:**

* [https://www.geeksforgeeks.org/quick-sort/](https://www.geeksforgeeks.org/quick-sort/)
* Thomas H. Cormen, Charles E. Leiserson, Ronald L. Rivest, and Clifford Stein. 2009. _Introduction to Algorithms_, Third Edition (3rd. ed.). The MIT Press
* [https://www.dei.unipd.it/\~geppo/AAD/DOCS/randomalgs.pdf](https://www.dei.unipd.it/\~geppo/AAD/DOCS/randomalgs.pdf)

