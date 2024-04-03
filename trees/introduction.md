---
description: Hierarchical data structure
---

# Introduction

A tree is an abstract data type that represents a hierarchical structure with a set of connected nodes. Each node in the tree may have numerous children, but must be connected to only one parent, except for the root, which has none.

More formally, a tree is a **maximal connected forest** with respect to a graph $$G=(V,E)$$.  A forest is an acylic partial graph $$G=(V,E^\prime)$$, it is maximal if every edge in $$E\backslash E^\prime$$ forms a cycle with the edges in $$E^\prime$$.

