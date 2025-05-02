# Optimal Substructure

{% hint style="info" %}
A problem exhibits optimal substructure when an optimal solution to the problem contains within it optimal solutions to subproblems
{% endhint %}

Dynamic programming builds an optimal solution to the problem from optimal solutions of subproblems.

Common pattern in identifying optimal substructure:

1. show that a solution consists of making a choice that leaves one or more subproblems
2. assume you are given the choice that leads to an optimal solution
3. given that choice, identify the subproblems that result from making that choice. Then, define how to represent these subproblems so you can describe the full set of subproblems you might need to solve.
4. show that the solution to the subproblems must be optimal, using contradiction. "Cut-and-paste" technique: "cut out" the nonoptimal solution and "paste in" the optimal one, and show that you can get a better solution to the original problem

Another key ingredient is that subproblems must be **independent**, meaning that the solution to one subproblem does not affect the solution to another subproblem of the same problem
