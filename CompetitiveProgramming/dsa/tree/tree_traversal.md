# Binary Tree Traversal

## Binary Tree
  ```c++
  Node *root = new Node(1);

  root->left = new Node(2);
  root->right = new Node(3);

  root->left->left = new Node(4);
  root->left->right = new Node(5);
  ```

## Depth First Traversal
### **Inorder** (left, root, right) - 4 2 5 1 3
  * recursive
  ```c++
  void inorder(Node * curr) {
      if(curr == NULL)
        return;
      inorder(curr->left);
      cout << curr->data << " ";
      inorder(curr->right);
  }
  ```
  * iterative
  ```c++
  void inorder(Node *root) {
      stack<Node*> s;
      Node *curr = root;

      while(curr != NULL || !s.empty()) {
        if(curr != NULL) {
          s.push(curr);
          curr = curr->left;
        }
        else {
          curr = s.top();
          s.pop();
          cout << curr->data << " ";
          curr = curr->right;
        }
      }
      cout << endl;
  }
  ```

###  **Preorder** (root left right) - 1 2 4 5 3
  * recursive
  ```c++
  void preorder(Node * curr) {
      if(curr == NULL)
          return;
      cout << curr->data << " ";
      preorder(curr->left);
      preorder(curr->right);
  }
  ```
  * iterative
  ```c++
  void preorder(Node *root) {
      stack<Node*> s;
      Node *curr = root;

      while(curr != NULL || !s.empty()) {
        if(curr != NULL) {
          cout << curr->data << " ";
          s.push(curr);
          curr = curr->left;
        }
        else {
          curr = s.top();
          s.pop();
          curr = curr->right;
        }
      }
      cout << endl;
  }
  ```

###  **Postorder** (left right root) - 4 5 2 3 1
  * recursive
  ```c++
  void postorder(Node * curr) {
      if(curr == NULL)
          return;
      postorder(curr->left);
      postorder(curr->right);
      cout << curr->data << " ";
  }
  ```
  * iterative
  ```c++
  ```

## Breath First Traversal

### **level order** - 1 2 3 4 5
