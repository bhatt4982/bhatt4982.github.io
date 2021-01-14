# Binary Tree

A binary tree is a tree data structure in which each node has at most two children, which are referred to as the left child and the right child.

* Each node contains three components:

  * Pointer to **left subtree**
  * Pointer to **right subtree**
  * **Data element**
```c++
  class Node {
  public:
      int data;
      Node *left, *right;

      Node(int val) {
        this->data = val;
        this->left = this->right = NULL;
      }
  };
```
