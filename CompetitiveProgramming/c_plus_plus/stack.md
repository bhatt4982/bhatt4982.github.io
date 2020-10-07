# Stack
* **LIFO**

## Construct

  ```c++

  // empty container constructor (default constructor)
  stack<int> s1;
  // s1 size - 0

  // empty stack using vector
  stack<int, vector<int>> s2;
  // s2 size - 0

  // stack initialized to copy vector
  vector<int> v{1, 2, 3, 4};
  stack<int, vector<int>> s3(v);
  // s3 size - 4

  // stack initialized to copy deque
  deque<int> d (3,100);
  stack<int> s4(d);
  // s4 size - 3
  ```

## Operations
* **empty** - Test whether container is empty
* **size** - Return size
* **top** - Access next element
* **push** - Insert element
* **pop** - Remove top element

  ```c++
  vector<int> v{1, 2, 3, 4};
  stack<int, vector<int>> s(v);
  cout << "empty - " << s.empty() << endl;
  // empty - 0
  cout << "size - " << s.size() << endl;
  // size - 4
  cout << "top - " << s.top() << endl;
  // top - 4
  s.top() += 10;
  cout << "top - " << s.top() << endl;
  // top - 14

  s.push(5);
  s.push(6);
  cout << "size - " << s.size() << ", top - " << s.top() << endl;
  // size - 6, top - 6

  s.pop();
  cout << "size - " << s.size() << ", top - " << s.top() << endl;
  // size - 5, top - 5
  ```
* **emplace** - Construct and insert element
  ```c++
  stack<pair<char, int>> s1;

  s1.push(pair<char, int>('a', 1));
  s1.emplace('b', 2);
  s1.emplace('b', 3);
  cout << "s1: size - " << s1.size() << endl;
  cout << "s1: top - (" << s1.top().first << ", " << s1.top().second << ")" << endl;
  // s1: size - 3
  // s1: top - (b, 3)
  ```
* **swap** - Swap contents
  ```c++
  deque<int> d1(4, 99);
  stack<int> s1(d1);
  cout << "s1: size - " << s1.size() << ", top - " << s1.top() << endl;
  // s1: size - 4, top - 99

  deque<int> d2(3,100);
  stack<int> s2(d2);
  cout << "s2: size - " << s2.size() << ", top - " << s2.top() << endl;
  // s2: size - 3, top - 100

  s1.swap(s2);
  cout << "s1: size - " << s1.size() << ", top - " << s1.top() << endl;
  // s1: size - 3, top - 100
  cout << "s2: size - " << s2.size() << ", top - " << s2.top() << endl;
  // s2: size - 4, top - 99
  ```
  ____
