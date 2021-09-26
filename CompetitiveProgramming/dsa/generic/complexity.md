# Algorithm Complexity

Algorithmic complexity is **a measure of how an algorithm would perform for the given input**

There are two kinds of complexities: **time and space.** Time complexity and space complexity are essentially approximations of how much time and how much space an algorithm will take to process certain inputs respectively.

## Notations

- Worst-case or upper bound: Big-O **O(n)**

* Best-case or lower bound: Big-Omega **Ω(n)**
* Average-case: Big-Theta **Θ(n)**

Developers typically solve for the worst case scenario, **Big O**

## Define Input Size

**Number Array: N**, where N is size of array

**String Array: N X K**, where N is size of array and K is size of string

**Matrix: M x N**, where M x N is size of matrix

**Linked List or Tree: N**, where N is number of nodes

**Graph: V- E**, having V vertices and E edges

## Types

* Constant Runtime **O(1)**
* Logarithmic Runtime **O(log n)**
* Linear Runtime **O(n)** **O(n log n)**
* Quadratic or Cubic Runtimes -  **O(n^2)** or **O(n^3)**
* Exponential Complexity -  **O(2^n)**, **O(10^n)** or **O(n!)**

$$
O(1)<O(logn)<O(√n)<O(n)<O(nlogn)<O(n^2)<O(n^3)<O(2^n)<O(10^n)<O(n!)
$$




| Input Size |  Worst Accepted Runtime  |
| :--------: | :----------------------: |
|    10^2    | O(N^6), O(N!) or O(2^N)  |
|    10^3    |     O(N^3) or O(N^4)     |
|    10^4    |          O(N^2)          |
|    10^5    |        O(N log N)        |
|    10^7    | O(N) or O(log N) or O(1) |

## Rules

* Ignore Constant

* Take the higher term

* Multi Part Algorithms



## Case Studies

### Recursive Runtimes

### Log N Runtimes



## Big O Notation Cheat Sheet

| Data Structure        | Worst Case Complexity                                        | Remark                                                       |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Array                 | Insert: O(1)<br />Access: O(1)<br />Search: O(n)             |                                                              |
| Linked List           | Insert: At head O(1) At Tail O(n)<br />Access: O(n)<br />Search: O(n) |                                                              |
| Binary Tree           | Insert: O(n)<br />Search: O(n)                               | In worst case, Binary tree becomes linked list. <br />Average case insert: O(logn) search: O(logn) |
| Stack/Queue           | Push/Enqueue: O(1)<br />Pop/Dequeue: O(1)                    |                                                              |
| Map/Set               | Search: O(1)                                                 |                                                              |
| Priority Queue (Heap) | Insert: O(logn)<br />Access: O(logn)                         |                                                              |
| B-Tree                | Insert: O(logn)<br />Access: O(logn)                         |                                                              |



| Algorithm      | Worst Case Complexity                                        | Average Case Complexity                                      | Remark  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------- |
| Sorting        | Bubble sort: O(n^2)<br/>Insertion sort: O(n^2)<br/>Selection sort: O(n^2)<br/>Quick sort: O(n^2)<br/>Merge sort: O(logn)<br />Heap sort: O(logn) | Bubble sort: O(n^2)<br/>Insertion sort: O(n^2)<br/>Selection sort: O(n^2)<br/>Quick sort: O(logn)<br/>Merge sort: O(logn)<br />Heap sort: O(logn) | n items |
| Tree Algorithm | Depth first search: O(n)<br/>Breadth first search: O(n)<br/>Traversals (Pre, in, post-order): O(n) |                                                              | n nodes |

