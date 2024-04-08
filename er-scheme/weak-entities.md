# Weak Entities

A **weak entity** is an entity which has the need of another entity to be identified completely.&#x20;

<figure><img src="../.gitbook/assets/Screenshot 2024-04-08 alle 15.57.37.png" alt=""><figcaption><p>Example of a weak entity</p></figcaption></figure>

In this example, since a place in a theater can have the same identifier in another theater, we need the theater itself to identify the place. Note that the weak entity must participate in the association with cardinality (1,1).



Also note that a weak entity can be made "strong" by adding a ID attribute, which can be convenient for efficiency, but may cause data consistency problems.
