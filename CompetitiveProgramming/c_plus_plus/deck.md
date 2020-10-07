# Deque
> * acronym of **double-ended queue**
> * pronounced like **deck**
> * provide a functionality similar to vectors, but with efficient insertion and deletion of elements also at the beginning of the sequence, and not only at its end.
> * unlike vectors, deques are not guaranteed to store all its elements in contiguous storage locations
> * accessing elements in a deque by offsetting a pointer to another element causes undefined behavior.

## Modifiers
* **assign** - Assign container content
  ```c++
  deque<int> first;
  deque<int> second;
  deque<int> third;

  first.assign (7,100);
  // 7 ints with a value of 100

  deque<int>::iterator it;
  it=first.begin()+1;

  second.assign (it,first.end()-1);
  // the 5 central values of first

  int myints[] = {1776,7,4};
  third.assign (myints,myints+3);
  // assigning from array
  ```
* **push_back** - Add element at the end
* **push_front** - Insert element at beginning
* **pop_back** - Delete last element
* **pop_front** - Delete first element
```c++
```
* **emplace_front** - Construct and insert element at beginning
* **emplace_back** - Construct and insert element at the end
```c++
```
