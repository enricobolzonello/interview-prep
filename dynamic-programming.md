# Dynamic Programming

Combines the correctness of complete search and efficiency of greedy algorithms.&#x20;

{% hint style="info" %}
Can be applied if the problem can be divided into overlapping subproblems that can be solved independently
{% endhint %}

Useful for:

* finding an optimal solution
* counting the number of solutions



There are two approaches:

* **bottom-up** (iterative), solve minimum subproblems and build up larger scale subproblems until we build the final result
* **top-down** (recursive), start from the original problem and search into subproblems. Usually implemented as DFS+memoization\
  The running time is always $$\text{work per subproblem} \times \text{number of subproblems}$$



Usually the chain of thought is as follows:

1. find the recurrence relation
2. write the recursive formulation
3. use memoization
4. find bottom up dynamic programming formulation

Let's take [https://leetcode.com/problems/min-cost-climbing-stairs/description/](https://leetcode.com/problems/min-cost-climbing-stairs/description/) as an example.&#x20;

The description states:

{% hint style="info" %}
You are given an integer array `cost` where `cost[i]` is the cost of `ith` step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index `0`, or the step with index `1`.

Return _the minimum cost to reach the top of the floor_.
{% endhint %}

which falls in finding the optimal solution where the relation is recursive. You can visualize the recursion like a DFS, where leafs are the end point. Let's do it step by step:

* find the recurrence relation\
  In this case it is $$\text{mincost}[i] = \text{cost}[i] + \min(\text{mincost}[i-1], \text{mincost}[i-2])$$\
  where the base cases are:&#x20;
  * $$\text{mincost}[0] = \text{cost}[0]$$
  * $$\text{mincost}[1] = \text{cost}[1]$$
* convert the relation to recursion (top-down)

<pre class="language-python"><code class="lang-python"><strong>        def rec(n):
</strong>            if n&#x3C;0:
                return 0
            if n==0 or n==1:
                return cost[n]
            return cost[n] + min(rec(n-1), rec(n-2))
            
        return min(rec(len(cost)-1), rec(len(cost)-2))
</code></pre>

* add memoization

```python
        def rec(n):
            if n<0:
                return 0
            if n==0 or n==1:
                return cost[n]
            if dp[n] != 0:
                return dp[n]
            dp[n] = cost[n] + min(rec(n-1), rec(n-2))
            return dp[n]
        n = len(cost)
        dp = [0] * n
        return min(rec(n-1), rec(n-2))
```

* convert to bottom up dynamic programming (iterative)

```python
        dp = [0] * len(cost)
        dp[0] = cost[0]
        dp[1] = cost[1]

        for i in range(2, len(cost)):
            dp[i] = cost[i] + min(dp[i-1], dp[i-2])
        return min(dp[-1], dp[-2])
```

Note that in this case you need only two memory cells at a time, so you can use two variables instead of a full array.













