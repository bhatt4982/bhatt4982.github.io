# MAP

* **unordered_map** - Key-Value pairs - ***not sorted***
* Elements are organized into buckets depending on their hash values
* unordered_map containers are faster than map containers to access individual elements by their key, although they are generally less efficient for range iteration through a subset of their elements.

## Container properties
* **Unordered**
___
## Iterators
> * iterators are at least forward iterators - **rbegin/crbegin** and **rend/crend** - **not supported**
___
## Element Lookup
* **find**
> * Complexity
    * **Average case: constant**
    * **Worst case: linear**
* **count**
> * Complexity
    * **Average case: linear**
    * **Worst case: linear**
