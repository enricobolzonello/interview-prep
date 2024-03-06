---
description: Technique to reduce the use of nested loops and replace it with a single loop
---

# Sliding Window

Different kinds of windows:

* **fast/slow** -> fast pointer that grows the window and a slow pointer that shrinks the window. Once you find a valid window with the fast pointer, slide the slow pointer until you no longer have a valid window
* **fast/catchup** -> similar to first, but when moving the slow pointer, you move it up the fast pointer's location
* **fast/lagging** ->  slow pointer is referencing one or two indices behind the fast pointer and it's keeping track of some choice you've made
* **front/back** ->  one pointer travels from the front, and the other from the back

## Templates

### Template 1: Shrinkable Sliding Window

```python
j = 0
for j in range(N):
    # use A[j] to update state which might make the window invalid
    while invalid():
        i = i+1
        # update state using A[i]
    ans = max(ans, j-i+1) # window [i,j] is the maximum window
return ans
```

### Template 2: Non-shrinkable Sliding Window

```python
j = 0
for j in range(N):
    # use A[j] to update state which might make the window invalid
    if invalid():
        i = i+1
        # update state using A[i]
    # window [i,j) might be valid
return j-i
```



**Problems:**

* [https://leetcode.com/problems/longest-substring-without-repeating-characters/](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
* [https://leetcode.com/problems/frequency-of-the-most-frequent-element/](https://leetcode.com/problems/frequency-of-the-most-frequent-element/)
* [https://leetcode.com/problems/permutation-in-string/](https://leetcode.com/problems/permutation-in-string/)
* [https://leetcode.com/problems/minimum-window-substring/](https://leetcode.com/problems/minimum-window-substring/)



**References:**

* [https://liuzhenglaichn.gitbook.io/algorithm/array/sliding-window](https://liuzhenglaichn.gitbook.io/algorithm/array/sliding-window)
* [https://stackoverflow.com/questions/8269916/what-is-sliding-window-algorithm-examples](https://stackoverflow.com/questions/8269916/what-is-sliding-window-algorithm-examples)
* [https://medium.com/outco/how-to-solve-sliding-window-problems-28d67601a66](https://medium.com/outco/how-to-solve-sliding-window-problems-28d67601a66)
