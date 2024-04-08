# Associations

An **association** establishes connections two or more entities. As for multi-value attributes, we can use two numbers to indicate the minimum and maximum number of elements of the other entities involved.



Associatons may also have attributes. From a  set-theoretic perspective, it doesn't change if an associations does have or not an attribute.&#x20;

## Recursive associations

A recursive association $$R$$ involves the same entity and is a subset of $$R\subseteq E_1\times E_1$$.



## N-ary associations

Association with more than two entities. Rarely you'll find associations with more than four entities involved.



As a particular example, suppose you have the scheme in the following figure:

<figure><img src="../.gitbook/assets/Screenshot 2024-04-08 alle 15.37.52.png" alt=""><figcaption><p>Ternary associations example</p></figcaption></figure>

This example models the fact that a musician can record a song and study an instrument.

But by the ER scheme, a musician can participate in a song with an instrument he doesn't know, which can't be possible in reality. To handle this fact, we need **additional documentation**.

### Trasform in binary associations

{% hint style="info" %}
Only when one of the entities takes part with **maximum cardinality one**
{% endhint %}

We consider this case through an example.

<figure><img src="../.gitbook/assets/Screenshot 2024-04-08 alle 15.45.41.png" alt=""><figcaption></figcaption></figure>

An employee works only for a project-location pair. It seems easy but depending on how we see it, the scheme changes.

For example:&#x20;

* is the project that has only one location? In this case, we can use two binary associations, one from project to location with (1,1) in the project part and the other from project to employee with cardinality (1,1) in the employee part
* is the location that has only one project? In this case, we have one binary association from project to location with cardinality (1,1) in the location part and the other association from location to employee with cardinality (1,1) in the employee part
* is the employee that works in only one location and it has only one project to work towards?

The right one is dictated by informations we have on the mini-world considered.
