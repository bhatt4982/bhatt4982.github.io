# Algorithm Complexity

Algorithmic complexity is **a measure of how an algorithm would perform for the given input**

## Define Input Size

**Number Array: N**, where N is size of array

**String Array: N X K**, where N is size of array and K is size of string

**Matrix: M x N**, where M x N is size of matrix

**Linked List or Tree: N**, where N is number of nodes

**Graph: V- E**, having V vertices and E edges

## Time Complexity

Algorithm runtime w.r.t. input size

## Space Complexity

Algorithm space requirement (memory footprint) w.r.t. input size

## Notations

- Worst-case or upper bound: Big-O **O(n)**

* Best-case or lower bound: Big-Omega **Ω(n)**

* Average-case: Big-Theta **Θ(n)**

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
