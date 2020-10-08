# Deque
> * acronym of **double-ended queue**
> * pronounced like **deck**
> * provide a functionality similar to vectors, but with efficient insertion and deletion of elements also at the beginning of the sequence, and not only at its end.
> * unlike vectors, deques are not guaranteed to store all its elements in contiguous storage locations
> * accessing elements in a deque by offsetting a pointer to another element causes undefined behavior.


  ```c++
  deque <int> dq;
  dq.push_back(10);
  dq.push_front(20);
  dq.push_back(30);
  dq.push_front(15);
  // dq - {15, 20, 10, 30}
  showdq(dq);

  cout << "dq.size() : " << dq.size() << endl;
  cout << "dq.max_size() : " << dq.max_size() << endl;
  // dq.size() : 4
  // dq.max_size() :4611686018427387903

  cout << "dq.at(2) : " << dq.at(2) << endl;
  cout << "dq.front() : " << dq.front() << endl;
  cout << "dq.back() : " << dq.back() << endl;
  // dq.at(2) : 10
  // dq.front() : 15
  // dq.back() : 30

  dq.pop_front();
  // dq - {20, 10, 30}

  dq.pop_back();
  // dq - {20, 10}
  ```
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
