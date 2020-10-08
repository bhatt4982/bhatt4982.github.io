# Queue
* **FIFO**

## Construct
  ```c++
  // empty container constructor (default constructor)
  queue<int> q1;
  // q1 size - 0

  // empty stack using list
  queue<int, list<int>> q2;
  // q2 size - 0

  // stack initialized to copy list
  list<int> l {1, 2, 3, 4};
  queue<int, list<int>> q3(l);
  // q3 size - 4

  // stack initialized to copy deque
  deque<int> d (3,100);
  queue<int> q4(d);
  // q4 size - 3
  ```
___
## Operations
* **empty** - Test whether container is empty
* **size** - Return size
* **front** - Access next element
* **back** - Access last element
* **push** - Insert element
* **pop** - Remove next element
  ```c++
  list<int> l{1, 2, 3, 4};
  queue<int, list<int>> q(l);
  cout << "empty - " << q.empty() << endl;
  // empty - 0
  cout << "size - " << q.size() << endl;
  // size - 4
  cout << "front - " << q.front() << endl;
  // front - 1
  cout << "back - " << q.back() << endl;
  // back - 4

  q.front() += 10;
  q.back() += 10;
  cout << "front - " << q.front() << ", back - " << q.back() << endl;
  // front - 11, back - 14

  q.push(5);
  q.push(6);
  cout << "size - " << q.size() << ", back - " << q.back() << endl;
  // size - 6,  back - 6

  q.pop();
  cout << "size - " << q.size() << ", back - " << q.back() << endl;
  // size - 5, top - 5
  ```
* **emplace** - Construct and insert element
  ```c++
  queue<pair<char, int>> q;

  q.push(pair<char, int>('a', 1));
  q.emplace('b', 2);
  q.emplace('b', 3);

  cout << "q: size - " << q.size() << endl;
  cout << "q: front - (" << q.front().first << ", " << q.front().second << ")" << endl;
  cout << "q: back - (" << q.back().first << ", " << q.back().second << ")" << endl;

  // q: size - 3
  // q: front - (a, 1)
  // q: back - (b, 3)
  ```    
* **swap** - Swap contents
  ```c++
  deque<int> d1(4, 99);
  stack<int> q1(d1);
  cout << "q1: size - " << q1.size() << endl;
  // q1: size - 4

  deque<int> d2(3,100);
  stack<int> q2(d2);
  cout << "q2: size - " << q2.size() << endl;
  // q2: size - 3

  q1.swap(q2);
  cout << "q1: size - " << q1.size() << endl;
  // s1: size - 3
  cout << "q2: size - " << q2.size() << endl;
  // q2: size - 4
  ```
____

# Priority Queue
* **Heap** implementation - default **MAX Heap**
* using **std::less** would cause the **largest** element to appear as the top() - default.
* using **std::greater** would cause the **smallest** element to appear as the top().

* template class definition
```c++
 template <
  class Type,
  class Container=vector<Type>,
  class Compare=less<typename Container::value_type> >
class priority_queue
```
* **MAX Heap**
  ```c++
  priority_queue<int> pq;
  // priority_queue<int, vector<int>, less<int>> pq;

  pq.push(10);
  pq.push(1);
  pq.push(100);
  pq.push(75);

  cout << "top() - " << pq.top() << endl;
  // top() - 100
  ```
* **MIN Heap**
  ```c++
  priority_queue<int, vector<int>, greater<int>> pq;

  pq.push(10);
  pq.push(1);
  pq.push(100);
  pq.push(75);

  cout << "top() - " << pq.top() << endl;
  // top() - 1
  ```
* **Custom** comparator - pass it as the third parameter of priority_queue template
  ```c++
  struct CustomCompare{
      bool operator()(const int& lhs, const int& rhs){
          return lhs < rhs;
      }
  };

  priority_queue<int, vector<int>, CustomCompare> pq;

  pq.push(10);
  pq.push(1);
  pq.push(100);
  pq.push(75);

  cout << "top() - " << pq.top() << endl;
  // top() - 100

  ```
