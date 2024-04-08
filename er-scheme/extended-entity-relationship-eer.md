---
description: Extension of the ER scheme to conveniently represent some situations
---

# Extended Entity Relationship (EER)

Everything that can be described by the EER can also be describe by a classic ER scheme, but with more hassle.

## IS-A Relation

{% hint style="info" %}
When an entity is a subset of another entity
{% endhint %}

When in a ER scheme, every instance of an entity is also an instance of another entity we have a **IS-A relation** between entities.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2024-04-08 alle 16.14.41.png" alt=""><figcaption><p>PERSONA is the father entity, while MUSICISTA is the son entity</p></figcaption></figure>

For this type of relation, the hereditary principle holds: every instance of the son entity has all the attributes of the father entity.

## Generalization and Specialization

{% hint style="info" %}
When an entity might have more than one son entity
{% endhint %}

In this case, we talk about **generalization** of a set of son entities or a **specialization** of a father entity.



A generalization can be:&#x20;

* **total**, each element of the father must be present in at least one son entity. The symbol is a full black arrow
* **partial**, there exist elements of the father that are not present in the son entities.&#x20;

Also:

* **disjoint**, the intersection of any pair of subsets is empty.
* **overlapped**, there exist at least one element shared by some  son entities.
