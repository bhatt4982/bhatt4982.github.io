# MAP

* **map** - Key-Value pairs ***ordered by Key***
* Maps are typically implemented as binary search trees.
* map containers are generally slower than unordered_map containers to access individual elements by their key, but they allow the direct iteration on subsets based on their order.
* Supports **bi-directional iterator**

## Container properties
* **Associative** - Elements referenced by their key and not by their absolute position in the container.
* **Ordered** -
* **Map** - Each element associates a key to a mapped value
* **Unique keys** - No duplicate keys
* **Allocator-aware** - dynamically handle its storage needs

____

## Constructor
  ```c++
  // empty container constructor (default constructor)
  map<char, int> first;
  // first - {}
  first['a'] = 1;
  first['b'] = 2;
  first['c'] = 3;
  // first - { ['a':1], ['b':2], ['c':3] }

  // range constructor
  map<char, int> second(first.begin(), first.end());
  // second - { ['a':1], ['b':2], ['c':3] }

  // copy constructor
  map<char, int> third(second);
  // third - { ['a':1], ['b':2], ['c':3] }

  // move constructor
  map<char, int> fourth( move(third) );
  // third - { }
  // fourth - { ['a':1], ['b':2], ['c':3] }
  ```
  ### Initialization
  ```c++
  map<char, int> fifth {
    {'x', 11},
    {'y', 12},
    {'z', 13}
  };
  // fifth - { ['x':11], ['y':12], ['z':13] }
  ```
  ### operator=
  ```c++
  map<char, int> sixth;
  sixth = fifth;
  // sixth - { ['x':11], ['y':12], ['z':13] }

  ```
___
## Capacity
* **empty** - Check if container is empty
* **size** - Return container size
* **max_size** - Return maximum size
  ```c++
  map<char, int> mymap {
    {'a', 1},
    {'b', 2}
  };

  cout << "Empty - " << mymap.empty() << endl;
  // empty - 0
  cout << "size - " << mymap.size() << ", max_size - " << mymap.max_size() << endl;
  // size - 2, max_size - 461168601842738790
  ```
___
## Element Access
* **operator[k]**
  > if k matches the key of an element in the container i.e. **key exists**, the function returns a reference to its mapped value.
  > if k does not match the key of any element in the container i.e. **key does not exists**, the function **inserts a new element** with that key and returns a reference to it mapped value.
  > Complexity - **Logarithmic**

  ```c++
  map<char, int> mymap {
    {'a', 1},
    {'b', 2}
  };
  // mymap - { {'a', 1}, {'b', 2}}
  mymap['a'] += 10;
  // mymap - { {'a', 11}, {'b', 2}}
  mymap['c'] = 3;
  // mymap - { {'a', 11}, {'b', 2}, {'c', 3}}

  ```
* **at(k)**
  > if k matches the key of an element in the container i.e. **key exists**, the function returns a reference to its mapped value.
  > if k does not match the key of any element in the container i.e. **key does not exists**, the function **throws an out_of_bound exception**
  > Complexity - **Logarithmic**

  ```c++
  map<char, int> mymap {
    {'a', 1},
    {'b', 2}
  };
  // mymap - { {'a', 1}, {'b', 2}}
  mymap.at('a') += 10;
  // mymap - { {'a', 11}, {'b', 2}}
  // mymap.at('c') = 3;
  // out_of_bound exception
  ```
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
  map<char, int> mymap {
    {'a', 1},
    {'b', 2},
    {'c', 3}
  };

  cout << "{ ";
  for(map<char, int>::iterator it = mymap.begin(); it != mymap.end(); ++it ) {
    cout << "{" << it->first << "," << it->second << "}, ";
  }
  cout << " }" << endl;
  // { {a,1}, {b,2}, {c,3},  }

  cout << "{ ";
  for(map<char, int>::const_iterator it = mymap.cbegin(); it != mymap.cend(); ++it ) {
    cout << "{" << it->first << "," << it->second << "}, ";
  }
  cout << " }" << endl;
  // { {a,1}, {b,2}, {c,3},  }

  cout << "{ ";
  for(map<char,int>::reverse_iterator it = mymap.rbegin(); it != mymap.rend(); ++it ) {
    cout << "{" << it->first << "," << it->second << "}, ";
  }
  cout << " }";
  // { {c,3}, {b,2}, {a,1},  }
  cout << "{ ";
  for(map<char,int>::const_reverse_iterator it = mymap.crbegin(); it != mymap.crend(); ++it ) {
    cout << "{" << it->first << "," << it->second << "}, ";
  }
  cout << " }";
  // { {c,3}, {b,2}, {a,1},  }

  ```
___

## Element Lookup
* **find(k)**

> * searches the container for an element with a key value equivalent to **k** and return the iterator to it if found.
> * Otherwise it returns an iterator to **map::end**
> * Complexity - **Logarithmic**

  ```c++
  map<char, int> mymap {
    {'a', 1},
    {'b', 2},
    {'c', 3}
  };

  map<char, int>::iterator it;
  it = mymap.find('a');
  if(it != mymap.end() )
    cout << "{" << it->first << ", " << it->second << "}" << endl;
  else
    cout << " Key 'a' not found..." << endl;
  // {a, 1}

  it = mymap.find('x');
  if(it != mymap.end() )
    cout << "{" << it->first << ", " << it->second << "}" << endl;
  else
    cout << "Key 'x' not found..." << endl;
  // Key 'x' not found..
  ```

* **count** - Count elements with a specific key
> *  searches the container for an element with a key value equivalent to **k** and return the number of matches
> * Due to unique key constraint, count returns **0(key does not exists) or 1(key exists)**
> * Complexity - **Logarithmic**

  ```c++
  map<char, int> mymap {
    {'a', 1},
    {'b', 2},
    {'c', 3}
  };

  cout << "Count of Key 'a' - " << mymap.count('a') << endl;
  //Count of Key 'a' - 1

  cout << "Count of Key 'x' - " << mymap.count('x') << endl;
  //Count of Key 'x' - 0

  ```

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
  map<char, int> mymap;
  // mymap - size = 0
  mymap.insert(pair<char, int> ('a', 1));
  mymap.insert(make_pair('b', 2));
  // mymap - { {'a', 1}, {'b', 2}}
  // mymap - size = 2

  pair<map<char, int>::iterator, bool> ret;
  ret = mymap.insert(make_pair('b', 3));
  if( ret.second == false) {
    cout << "Key 'b' exists with value - " << ret.first->second << endl;
  }
  // mymap - { {'a', 1}, {'b', 2}}
  // Key 'b' exists with value - 2

  mymap.insert(make_pair('c', 3));
  mymap.insert(make_pair('d', 4));
  // mymap - size = 4

  // insert with hint
  mymap.insert(mymap.begin(), make_pair('e', 5));
  mymap.insert(mymap.end(), make_pair('f', 6));
  // mymap - size = 6

  // erase by key
  mymap.erase('c');
  // mymap - size = 5

  // erase by iterator
  auto it = mymap.find('d');
  mymap.erase(it);
  // mymap - size = 4

  // erase by range
  mymap.erase(mymap.begin(), mymap.find('e'));
  // from start upto key 'e'
  // mymap - size = 2
  ```
* **swap** - Swap content
  ```c++
  map<char, int> mymap {
    {'a', 1},
    {'b', 2}
  };
  // mymap size - 2
  map<char, int> othermap {
    {'x', 11},
    {'y', 12},
    {'z', 13}
  };
  // othermap size - 2
  mymap.swap(othermap);
  // mymap size - 3
  // othermap size - 2
  ```
* **clear** - Clear content
  ```c++
  map<char, int> mymap {
    {'a', 1},
    {'b', 2}
  };
  // mymap size - 2
  mymap.clear();
  // mymap size - 0
  ```
* **emplace** - Construct and insert element
* **emplace_hint** - Construct and insert element with hint
  ```c++
  map<char, int> mymap;
  // mymap size - 0
  mymap.emplace('a', 1);
  // mymap size - 1
  mymap.emplace_hint(mymap.begin(), 'b', 2);
  // mymap size - 2
  cout << "mymap size - " << mymap.size() << endl;
  ```
