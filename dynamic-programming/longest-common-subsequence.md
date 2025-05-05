# Longest Common Subsequence

{% hint style="info" %}
A subsequence is the given sequence with 0 or more elements left out
{% endhint %}

A sequence Z is a common subsequence of X and Y if Z is a subsequence of both X and Y. The goal is to find a maximum-length common subsequence of X and Y.

LCS has an optimal substructure, as proved by the following theorem:

> Let $$X=\lang x_1,...,x_m\rang$$ and $$Y=\lang y_1,...,y_n\rang$$ be sequences, and let $$Z=\lang z_1,...,z_k\rang$$ be any lcs of X and Y. Then:&#x20;
>
> 1. if $$x_m =y_n$$, then $$z_k=x_m=y_n$$ and $$Z_{k-1}$$ is an lcs of $$X_{m-1}$$ and $$Y_{n-1}$$
> 2. if $$x_m \ne y_n$$ and $$z_k\ne x_m$$ then $$Z$$ is an lcs of $$X_{m-1}$$ and $$Y$$&#x20;
> 3. if $$x_m \ne y_n$$ and $$z_k\ne y_n$$ then $$Z$$ is an lcs of $$X$$ and $$Y_{n-1}$$

The optimal substructure of the lcs problem gives the recursive formula:

$$
c[i,j]=\begin{cases}0&\text{if }i=0\text{ or }j=0\\ c[i-1,j-1]+1 & \text{if }i,j>0 \text{ and }x_i=y_j\\ \max\{c[i,j-1],c[i-1,j]\} & \text{if }i,j>0 \text{ and }x_i\ne y_j\end{cases}
$$

The recursive implementation is straightforward but inefficient. Instead a top-down formulation exists:

```python
class Solution:
        def longestCommonSubsequence(self, s1: str, s2: str) -> int:
            m = len(s1)
            n = len(s2)
            memo = [[0 for _ in range(n + 1)] for _ in range(m + 1)]
    
            for row in range(1, m + 1):
                for col in range(1, n + 1):
                    if s1[row - 1] == s2[col - 1]:
                        memo[row][col] = 1 + memo[row - 1][col - 1]
                    else:
                        memo[row][col] = max(memo[row][col - 1], memo[row - 1][col])
    
            return memo[m][n]
```

Note that in each step the execution depends on three values:

* $$(row-1,col-1)$$
* $$(row,col-1)$$
* $$(row-1,col-1)$$

so the table can be thrown out and instead we just keep three variables, bringing down space complexity to $$O(1)$$.
