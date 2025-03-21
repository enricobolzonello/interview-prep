---
description: Greedy/dp algorithm to find a non-empty subarray with the largest sum
---

# Kadane's Algorithm

{% hint style="info" %}
Find a non-empty subarray with the largest sum
{% endhint %}

Brute force approach takes $$O(n^2)$$ time, which is not the most efficient.



INTUITION:

1. if all elements are positive, the maximum sum is the entire array
2. we want to avoid the negative sum subarray



```python
def max_subarray_sum(nums):
    maxSum = nums[0]
    curSum = 0
    
    for n in nums:
        curSum = max(curSum, 0)
        curSum += n
        maxSum = max(maxSum, curSum)
    return maxSum
```



### Return the actual subarray

use sliding window.

```python
def slidingWindow(nums):
    maxSum = nums[0]
    curSum = 0
    maxL, maxR = 0, 0
    L = 0

    for R in range(len(nums)):
        if curSum < 0:
            curSum = 0
            L = R

        curSum += nums[R]
        if curSum > maxSum:
            maxSum = curSum
            maxL, maxR = L, R 

    return [maxL, maxR]
```



Time: $$O(n)$$

Space: $$O(1)$$

