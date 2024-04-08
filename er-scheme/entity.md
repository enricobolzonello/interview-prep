# Entity

The **entity** is the base element of the ER model which represents a class of objects of the mini-world we want to represent.

<figure><img src="../.gitbook/assets/Screenshot 2024-04-04 alle 17.02.17.png" alt=""><figcaption><p>MUSICISTA Entity</p></figcaption></figure>

## Attributes

* **simple**
* **composite** -> one or more simple attributes combined into one
* **multi-value** -> an attribute may hold multiple values, represented as the simple attribute with (n,m) near it where n represents the minimum number of values the attribute can have and m the maximum

## Identifier

We want to find a minimum subset of attributes which identify the elements. The choice must be independent of the specific data sample we have available but should hold true for all possible sets of elements of that entity.



In some cases, the identifier might be a composite attribute, in others, it may have multiple identifiers.
