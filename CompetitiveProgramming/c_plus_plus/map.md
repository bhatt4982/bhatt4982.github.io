# MAP

* **map** - Key-Value pairs ***ordered by Key***
* Maps are typically implemented as binary search trees.
* map containers are generally slower than unordered_map containers to access individual elements by their key, but they allow the direct iteration on subsets based on their order.

## Container properties
* **Associative** - Elements referenced by their key and not by their absolute position in the container.
* **Ordered** -
* **Map** - Each element associates a key to a mapped value
* **Unique keys** - No duplicate keys
* **Allocator-aware** - dynamically handle its storage needs

____

## Constructor
```c++
````
### operator=
```c++
````
### Initialization
```c++
````
___
## Capacity
* **empty** - Check if container is empty
* **size** - Return container size
* **max_size** - Return maximum size
```c++
````
___
## Iterators
  * **begin** - Return iterator to beginning
  * **end** - Return iterator to end
  * **cbegin** - Return const_iterator to beginning
  * **cend** - Return const_iterator to end
  * **rbegin** - Return reverse iterator to reverse beginning
  * **rend** - Return reverse iterator to reverse end
  * **crbegin** - Return reverse const_iterator to reverse beginning
  * **crend** - Return reverse const_iterator to reverse end
```c++
```
___
## Element Access
* **operator[]**
* **at**

```c++
````
___
## Element Lookup
* **find** - Get iterator to element

> * Complexity - **Logarithmic**

```c++
````

* **count** - Count elements with a specific key
> * Complexity - **Logarithmic**

```c++
````

* **equal_range** - Get range of elements with specific key


```c++
````

* **lower_bound** - Return iterator to lower bound
* **upper_bound** -Return iterator to upper bound
```c++
````
___
## Modifiers
* **insert** - Insert elements
* **erase** - Erase elements
```c++
````
* **swap** - Swap content
```c++
````
* **clear** - Clear content
```c++
````
* **emplace** - Construct and insert element
* **emplace_hint** - Construct and insert element with hint
```c++
````
