## Data Structures
**Linked List**
* A LL is a linear collection of data elements, called nodes, each pointing to the next node by means of a pointer. It is a data structure consisting of a group of nodes which together represent a sequence.
* **Singly LL:** LL in which each node points to the next node and the last node points to null
* **Doubly LL:** LL in which each node has two pointers, p and n, such that p points to the previous node and n points to the next node; the last node's n pointer points to null
* **Circular LL:** LL in which each node points to the next node and the last node points back to the first node
* Time Complexity:
  * Access: ``` O(n) ```
  * Search: ``` O(n) ```
  * Insert: ``` O(1) ```
  * Remove: ``` O(1) ```

**Stack**
* A Stack is a collection of elements, with two principle operations: push, which adds to the collection, and pop, which removes the most recently added element.
* **LIFO data structure:** the most recently added object is the first to be removed
* Time Complexity:
  * Access: ``` O(n) ```
  * Search: ``` O(n) ```
  * Insert: ``` O(1) ```
  * Remove: ``` O(1) ```

**Queue**

* A Queue is a collection of elements, supporting two principle operations: enqueue, which inserts an element into the queue, and dequeue, which removes an element fromt he queue
* **FIFO data structure:** the oldest added object is the first to be removed
* Time Complexity:
  * Access: ``` O(n) ```
  * Search: ``` O(n) ```
  * Insert: ``` O(1) ```
  * Remove: ``` O(1) ```
    
**Tree**
* A Tree is an undirected, connected, acyclic graph

**Binary Tree**
*  A Binary Tree is a tree data structure in which each node has at most two children, which are referred to as the left child and the right child
*  **Full tree:** a tree in which each node has either 0 or 2 children
*  **Perfect Binary Tree:** a binary tree in which all interior nodes have two children and all leave have the same depth
*  **Complete Tree:** a binary tree in which every level except possibly the last is full and all nodes in the last level are as far left as possible

**Binary Search Tree**  
* A BST is a type of  binary tree which maintains the property that the value in each node must be greater than or equal to any value stored in the left sub-tree, and less thn or equal to any value stored in the right sub-tree <img src = "https://github.com/user-attachments/assets/c1407068-d57a-4e23-b823-9f47c51c52f5" width="120" align="right"/>


* Time Complexity:
   * Access: ``` O(log(n)) ```
  * Search: ``` O(log(n)) ```
  * Insert: ``` O(log(n)) ```
  * Remove: ``` O(log(n)) ```
 
    
**Trie**
* A Trie, sometimes called a radix or prefix tree, is a kind of search tree that is used to store a dynamic set or associative array where the keys are usually strings. No node in the tree stores the key associated with that node; instead, its position in the tree defines the key with which it is associated. All the descendants of a node have a common prefix of the string associated with that node, and the root is associated with the empty string.
 <img src = "https://github.com/Kranthi-Guribilli/Daily-Byte/blob/main/images/trie.png" width="200" align="center"/>

  
**Fenwick Tree**
* A Fenwick tree, sometimes called a binary indexed tree, is a tree in concept, but in practice is implemented as an implicit data structure using an arry. Given an index in the array representing a vertex, the index of a vertex's parent or child is calculated through bitwise operations on the binary representation of its index. Each element of the array contains the pre-calculated sum of a range of values, and by combining that sum with additional ranges encountered during an upward traversal to the root, the prefix sum is calculated
* Time Complexity:
  * Range Sum: ``` O(log(n)) ```
  * Update: ``` O(log(n)) ```
  <img src = "https://github.com/Kranthi-Guribilli/Daily-Byte/blob/main/images/fenwickTree.png" align="center"/>
