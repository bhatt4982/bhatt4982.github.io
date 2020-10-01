# Vector

## Container properties
  * **Sequence** - ordered in a strict linear sequence
  * **Dynamic array** - direct access to any element
  * **Allocator-aware** - dynamically handle its storage needs

___

## Constructor
```c++
    // empty container constructor (default constructor)
    vector<int> a;
    // a - []

    // fill constructor
    vector<int> b(4, 100);
    // b - [100, 100, 100, 100]

    // range constructor
    vector<int> c(b.begin(), b.end());
    // c - [100, 100, 100, 100]

    // copy constructor
    vector<int> d(c);
    // d - [100, 100, 100, 100]
```
### operator=
```c++
    std::vector<int> p(3, 0);
    // p - [0, 0, 0]
    std::vector<int> q(5, 1);
    // q - [1, 1, 1, 1, 1]
    p = q;
    // p - [1, 1, 1, 1, 1]
```

### Initialization

```c++
    vector<int> a{1, 2, 3, 4}; // a - [1, 2, 3, 4]

    int raw[] = { 1, 2, 3, 4 };
    vector<int> b(raw, raw + sizeof(raw) / sizeof(int)); // b - [1, 2, 3, 4]
```
___

## Element access
* **operator[]** - Returns a reference to the element at specified location pos. No bounds checking is performed.
* **at** - Returns a reference to the element at specified location pos, with bounds checking.
* **front** - Returns a reference to the first element in the container. Calling front on an empty container is undefined.
* **back** - Returns a reference to the last element in the container. Calling back on an empty container causes undefined behavior.
* **data** - Returns pointer to the underlying array serving as element storage. If size() is 0, data() may or may not return a null pointer.
```c++
    vector<int> x{ 1, 2, 3, 4 };
    cout << "element [2] - " << x[2] << endl;
    cout << "element at 3 - " << x.at(3) << endl;

    cout << "element at front - " << x.front() << endl;

    cout << "element at back - " << x.back() << endl;

    int* pX = x.data();
    cout << "element at 3 - " << pX[3] << endl;
```
___

## Capacity
* **size** - number of actual objects held
* **capacity** - size of the storage space currently allocated
* **max_size** - maximum potential size(by no means guaranteed)
```c++
    vector<char> t1;
    cout << "T1" << endl;
    cout << "Size: " << t1.size() << ", Capacity: " << t1.capacity() << ", Max Size: " << t1.max_size() << endl;
    cout << endl;

    vector<char> t2(10);
    cout << "T2" << endl;
    cout << "Size: " << t2.size() << ", Capacity: " << t2.capacity() << ", Max Size: " << t2.max_size() << endl;
    cout << endl;

    vector<int> t3;
    cout << "T3" << endl;
    cout << "Size: " << t3.size() << ", Capacity: " << t3.capacity() << ", Max Size: " << t3.max_size() << endl;

    for (int i = 0; i < 10; i++) {
        t3.push_back(i);
        cout << "Size: " << t3.size() << ", Capacity: " << t3.capacity() << endl;
    }
    cout << endl;
```
* **resize** - Resizes the container so that it contains n elements.
```c++
    vector<int> t4(2);
    cout << "T4" << endl;
    cout << "Initial Size: " << t4.size() << ", Initial Capacity: " << t4.capacity() << endl;
    t4.resize(50);
    cout << "After resize(50) - Size: " << t4.size() << ", Capacity: " << t4.capacity() << endl;
    t4[49] = 7;
    t4.resize(10);
    cout << "After resize(10) - Size: " << t4.size() << ", Capacity: " << t4.capacity() << endl;
    cout << endl;
```
* **reserve** - Requests that the vector capacity be at least enough to contain n elements.
```
    vector<int> t5(12);
    cout << "T5" << endl;
    cout << "Initial Size: " << t5.size() << ", Initial Capacity: " << t5.capacity() << endl;
    t5.reserve(50);
    cout << "After reserve(50) - Size: " << t5.size() << ", Capacity: " << t5.capacity() << endl;
    // t5[49] = 7; // - Exception vector subscript out of range
    t5.reserve(10);
    cout << "After reserve(10) - Size: " << t5.size() << ", Capacity: " << t5.capacity() << endl;
    cout << endl;
```
* **shrink_to_fit** - Requests the container to reduce its capacity to fit its size.
```c++
    vector<int> t6(12);
    t6.reserve(1000);
    cout << "T6" << endl;
    cout << "Initial Size: " << t6.size() << ", Initial Capacity: " << t6.capacity() << endl;
    t6.shrink_to_fit();
    cout << "After shrink_to_fit() - Size: " << t6.size() << ", Capacity: " << t6.capacity() << endl;
    cout << endl;
```
* **empty** - Returns whether the vector is empty (i.e. whether its size is 0).
```c++
    vector<int> t7;
    cout << "T7 empty - " << t7.empty() << endl; \\ 1
    t7.resize(5);
    cout << "T7 empty - " << t7.empty() << endl; \\ 0
```
___

## Iterators
  * **begin** - Return iterator to beginning
  * **end** - Return iterator to end
  * **cbegin** - Return const_iterator to beginning
  * **cend** - Return const_iterator to end

```c++
    vector<int> r{ 1, 2, 3, 4 };
    for (vector<int>::iterator it = r.begin(); it != r.end(); it++)
        cout << *it << " ";
    cout << endl;

    for (auto it = r.rbegin(); it != r.rend(); it++)
        cout << *it << " ";
    cout << endl;

    for (vector<int>::const_iterator it = r.cbegin(); it != r.cend(); it++)
        cout << *it << " ";
    cout << endl;

    for (auto it = r.crbegin(); it != r.crend(); it++)
        cout << *it << " ";
    cout << endl;

    auto it = r.begin();
    *it += 10;

    cout << "Updated value r[0] - " << r[0] << endl;

    auto it1 = r.cbegin();
    // *it1 += 10; //- compile time error - you cannot assign to a variable that is const
```
___

## Modifiers
* **push_back** - Appends the given element value to the end of the container.
* **pop_back** - Removes the last element of the container.
```c++
    vector<int> m; // creates empty array

    m.push_back(1); // m - [1]
    m.push_back(2); // m - [1, 2]
    m.push_back(3); // m - [1, 2, 3]

    m.pop_back(); // m - [1, 2]
    m.pop_back(); // m - [1]
    m.pop_back(); // m - []
```
* **insert** - Inserts elements at the specified location in the container
* **erase**
```c++
    vector<int> n{ 1, 2, 3 }; // n - [1, 2, 3]
    auto it = n.begin();
    n.insert(it, 5); // n - [5, 1, 2, 3]
    // "it" no longer valid, get a new one:
    it = n.begin();
    n.insert(it + 1, 6); // n - [5, 6, 1, 2, 3]
    n.insert(n.begin(), 2, 10); // n - [10, 10, 5, 6, 1, 2, 3]

    int arr[] = { 51, 52, 53 };
    n.insert(n.end(), arr, arr+3); // n - [10, 10, 5, 6, 1, 2, 3, 51, 52, 53]

    vector<int> o;
    o.insert(o.begin(), n.begin() + 4, n.end() - 3); // o - [1, 2, 3]

    // erase
    n.erase(n.begin()); // n - [10, 5, 6, 1, 2, 3, 51, 52, 53]
    n.erase(n.begin() + 3, n.begin() + 6); // n - [10, 5, 6, 51, 52, 53]
    // Erase all even numbers (C++11 and later)
    for (auto it = n.begin(); it != n.end();) {
        if (*it % 2 == 0) {
            it = n.erase(it);
        }
        else {
            ++it;
        }
    }
    // m - []
    // n - [5, 51, 53]
    // o - [1, 2, 3]
```
* **swap** - Exchanges the contents of the container with those of other. Does not invoke any move, copy, or swap operations on individual elements
```c++
    n.swap(o);
    // o - [5, 51, 53]
    // n - [1, 2, 3]
```
* **clear** - Erases all elements from the container. After this call, size() returns zero.
```c++
    m.clear(); // m - []
    n.clear(); // n - []
    o.clear(); // o - []
```
* **emplace** - Construct and insert element - The container is extended by inserting a new element at position. This new element is constructed in place using args as the arguments for its construction.
* **emplace_back**
```c++
    vector<pair<int, int>> m; // creates empty array
    m.insert(m.begin(), make_pair(1, 2)); // m - [ (1,2) ]
    m.emplace(m.end(), 3, 4); // m - [ (1,2), (3,4) ]

    // emplace_back - emplace at end
    m.push_back(make_pair(5, 6)); // m - [ (1,2), (3,4), (5, 6) ]
    m.emplace_back(7, 8); // m - [ (1,2), (3,4), (5, 6), (7,8) ]
```
___
