---
description: >-
  Linear data structure where each element are linked together by the reference
  fields
---

# Linked List

```python
class ListNode:
    def __init__(self, val=0, next_node=None):
        self.val = val
        self.next_node = next_node
```



## Adding a Node

if we want to add a new value after a given node `prev`, we should:

* initialize a new node with the given value
* link the `next_node` field of the new node to prev's `next_node`
* link the `next_node` field in prev to the new node

Time Complexity: `O(1)`, if we have a reference to `prev`



## Delete a Node

We can do it in two steps:

* find node to remove previous node `prev_node` and its next node `next_node`
* link `prev_node` to cur's next node `next_node`

Since we have to traverse the linked list to find `prev_node`, the time complexity is `O(N)`



## Floyd's Cycle-Finding algorithm

```python
def floyd(head):
    slow, fast = head, head
    
    while slow != None and fast != None and fast.next != None:
        slow = slow.next
        fast = fast.next.next
        
        if slow == fast:
            return True
    
    return False
```

Let $$L$$ denote the length of the cycle and $$a$$ the number of steps required for the slow pointer to reach the entry of the cycle.

There exists $$k>0$$ such that $$k\cdot L\ge a$$. When the slow pointer has moved $$k\cdot L$$ steps and the fast pointer has covered $$2 k L$$ steps, both pointers find themselves within the cycle.

At this point there is a $$kL$$ separation between them. Given that the cycle's length remains $$L$$, this means that they meet at the same point within the cycle.



### Find the Starting Point of the Cycle

To find the starting point of the cycle add this code:

<pre class="language-python"><code class="lang-python">slow = head
<strong>while slow != fast:
</strong>    slow = slow.next
    fast = fast.next.next
return slow
</code></pre>

Let's calculate the distance covered by both pointers until they met in the cycle:

$$
dist_{slow} = a+xL+b\\
dist_{fast} = a+yL+b
$$

where $$a$$ is the number of steps that both pointers need to take to enter the cycle, $$b$$ is the distance between the start of the cycle and the meeting point of the pointers, $$x$$is the number of times the slow pointer has looped and $$y$$is the number of times the fast pointer has looped.

Knowing that $$dist_{fast} = 2dist_{slow}$$, we get:

$$
a+yL+b=2(a+xL+b)
$$

and solving by a we obtain $$a=(y-2x)L-b$$, which means that doing $$a$$ steps is the same as doing $$y-2x$$ loops and go $$b$$ steps backwards.&#x20;

Since the fast pointer is $$b$$ steps ahead of the entry of the cycle, if the fast pointer moves $$a$$ steps it will end up at the entry of the cycle. Since the slow starts at the begin of the linked list it is sufficient to make $$a$$ steps to find the cycle entry, meaning that when the two pointers meet we found the beginning of the cycle.



## Find Middle Element

```python
slow, fast = head, head
while fast and fast.next:
    slow = slow.next
    fast = fast.next
mid = slow
```

Also called Two-Pointer or Tortoise-and-Hare algorithm



## Reverse Linked List

```python
prev, curr = None, slow.next
        while curr:
            next_node = curr.next
            curr.next = prev
            prev = curr
            curr = next_node
```





**Problems:**

* [https://leetcode.com/problems/linked-list-cycle/description/](https://leetcode.com/problems/linked-list-cycle/description/)
* [https://leetcode.com/problems/palindrome-linked-list/description/](https://leetcode.com/problems/palindrome-linked-list/description/)
* [https://leetcode.com/problems/find-the-duplicate-number/description/](https://leetcode.com/problems/find-the-duplicate-number/description/)



**References:**

* [https://cp-algorithms.com/others/tortoise\_and\_hare.html](https://cp-algorithms.com/others/tortoise\_and\_hare.html)
* [https://leetcode.com/explore/learn/card/linked-list](https://leetcode.com/explore/learn/card/linked-list)



