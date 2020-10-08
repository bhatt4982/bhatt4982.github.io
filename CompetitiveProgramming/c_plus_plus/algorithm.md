# STL algorithm

## Traversal
  ```c++
  vector<int> a{10, 1, 100, 75};
  for(int x: a) {
    cout << x << ", ";
  }
  cout << endl;
  // 10, 1, 100, 75,

  ```
## sort
  ```c++
  vector<int> a{10, 1, 100, 75};
  sort(a.begin(), a.end());
  // a - 1, 10, 75, 100,
  ```
## reverse
  ```c++
  vector<int> a{10, 1, 100, 75};
  reverse(a.begin(), a.end());
  // a - 75, 100, 1, 10
  ```

## swap
  ```c++
  vector<int> a(3, 10), b(4, 20);
  // a: size - 3
  // b: size - 4
  swap(a, b);
  // a: size - 4
  // b: size - 3
  ```
## copy
  ```c++
  vector<int> a(3, 10), b(3, 0);
  // a - 10, 10, 10
  // b - 10, 10, 10
  copy(a.begin(), a.end(), b.begin());
  // a - 10, 10, 10
  // b - 10, 10, 10
  ```

## move
  ```c++
  vector<int> a(3, 10), b(3, 0);
  // a - 10, 10, 10
  // b - 0, 0, 0
  b = move(a);
  // a -
  // b - 10, 10, 10
  ```
## fill
  ```c++
  vector<int> a (5, 0);
  fill (a.begin(), a.begin()+2, 2);
  // a - 2, 2, 0, 0, 0
  ```

## generate
  ```c++
  int RandomNumber () { return (std::rand()%100); }

  vector<int> a (3);
  generate (a.begin(), a.end(), RandomNumber);
  // a - 83, 86, 77
  ```

## rotate
  * rotate(first, middle, last)
  * Rotates the order of the elements in the range [first,last), in such a way that the element pointed by middle becomes the new first element.

  ```c++
  vector<int> a {1, 2, 3, 4, 5};
  rotate(a.begin(), a.begin()+2, a.end());
  // 3, 4, 5, 1, 2
  ```
  ```c++
  vector<int> a {1, 2, 3, 4, 5};
  rauto it = find(a.begin(), a.end(), 3);
  rotate(a.begin(), it, a.end());
  // 3, 4, 5, 1, 2
  ```
