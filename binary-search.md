---
description: >-
  Search algorithm that finds the target within a sorted array, by repeatedly
  dividing the search interval in half.
---

# Binary Search

Works in $$O(\log N)$$ time with $$O(1)$$auxiliary space

## Templates

### Template 1

```python
def binarysearch(arr, left, right, target):
    while left <= right:
        mid = left + (right-left)//2
        
        if arr[mid] == target:
            return mid
        elif arr[mid] < x:
            left = mid+1
        else:
            right = mid-1
    return -1
```

Attributes:&#x20;

* search condition can be determined without comparing to the element's neighbors
* no post-processing, if you reach the end you know the element is not found

### Template 2

```python
def binarySearch(nums, target):
    if len(nums) == 0:
        return -1

    left, right = 0, len(nums) - 1
    while left < right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid + 1
        else:
            right = mid

    # Post-processing:
    # End Condition: left == right
    if nums[left] == target:
        return left
    return -1

```

Attributes:

* use the element's right neighbor to determine if the condition is met and decide whether to go left or right
* guarantees that the search space is at least 2 in size at each step
* post-processing required

### Template 3

```python
def binarySearch(nums, target):
    if len(nums) == 0:
        return -1

    left, right = 0, len(nums) - 1
    while left + 1 < right:
        mid = (left + right) // 2
        if nums[mid] == target:
            return mid
        elif nums[mid] < target:
            left = mid
        else:
            right = mid

    # Post-processing:
    # End Condition: left + 1 == right
    if nums[left] == target: return left
    if nums[right] == target: return right
    return -1
```

Attributes:

* use the element's neighbors to determine if the condition is met and decide whether to go left or right
* guarantees that the search space is at least 2 in size at each step
* post-processing required



Problems:

* [https://leetcode.com/problems/binary-search/](https://leetcode.com/problems/binary-search/)
* [https://leetcode.com/problems/sqrtx/description/](https://leetcode.com/problems/sqrtx/description/)
* [https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/)
* [https://leetcode.com/problems/search-a-2d-matrix/description/](https://leetcode.com/problems/search-a-2d-matrix/description/)



## Binary Answer

We can exploit te monotonicity of integer values to find a solution with binary search which requires $$O(n\log n)$$ time instead of the $$O(n)$$ time of a linear scanning.

We can use it if we can write a predicate function `valid(i)` that has **monotonicity**:&#x20;

<figure><img src=".gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>

The algorithm is the usual binary search, but with the difference of the `valid` function, defined based on the problem:

```python
def binaryanswer(minVal, maxVal):
    left, right = minVal, maxVal
    while left <= right:
        mid = left + (right-left)//2
        if valid(mid):
            left = mid+1
        else:
            right = mid-1
    return right >= minVal ? R : -1
```

Problems:

* [https://leetcode.com/problems/koko-eating-bananas/](https://leetcode.com/problems/koko-eating-bananas/)
* [https://leetcode.com/problems/minimum-speed-to-arrive-on-time/](https://leetcode.com/problems/minimum-speed-to-arrive-on-time/)





***

References:

* [https://leetcode.com/explore/learn/card/binary-search/](https://leetcode.com/explore/learn/card/binary-search/)
* [https://liuzhenglaichn.gitbook.io/algorithm/binary-answer](https://liuzhenglaichn.gitbook.io/algorithm/binary-answer)
