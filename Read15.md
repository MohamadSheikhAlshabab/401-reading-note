# Trees [URL](https://github.com/MohamadSheikhAlshabab/401-reading-note/blob/master/Read15.md)

## Common Terminology:

 - 1 - Node - A node is the individual item/data that makes up the data structure
 - 2 - Root - The root is the first/top Node in the tree
 - 3 - Left Child - The node that is positioned to the left of a root or node
 - 4 - Right Child - The node that is positioned to the right of a root or node
 - 5 - Edge - The edge in a tree is the link between a parent and child node
 - 6 - Leaf - A leaf is a node that does not contain any children
 - 7 - Height - The height of a tree is determined by the number of edges from the root to the bottommost node
 
 - __Sample Tree__:
  -  ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/BinaryTree1.PNG)
  - Traversals:
   - allows us to search for a node, print out the contents of a tree, and much more! 
   -  two categories of traversals: 
      - 1 - Depth First: is where we prioritize going through the depth (height) of the tree first.
        -  three methods for depth first traversal:
          - Pre-order: root >> left >> right
          - In-order: left >> root >> right
          - Post-order: left >> right >> root
          - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/tree-example.png)
   
   - 2 - Breadth First: Breadth first traversal iterates through the tree by going through each level of the tree node-by-node. 
      - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/tree-example.png)
      - Output: A, B, C, D, E, F
      - breadth first traversal uses a queue (instead of the call stack via recursion) to traverse the width/breadth of the tree. Let’s break down the process.
      -  putting the root into the queue:
        - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/BreadthTraversal1.PNG)
      - we can dequeue it and use that node in our code.
      - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/BreadthTraversal2.PNG)
 ---
 ## Binary Trees:
   - Trees can have any number of children per node, but Binary Trees restrict the number of children to two (hence our left and right children).
   - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/BinaryTree2.PNG).
 - __Adding a node__:
  - One strategy for adding a new node to a binary tree is to fill all “child” spots from the top down. To do so, we would leverage the use of breadth first traversal.
  - During the traversal, we find the first node that does not have 2 child nodes, and insert the new node as a child. We fill the child slots from left to right.
- __Big O__:
  - The Big O time complexity for inserting a new node is O(n). 
  - Searching for a specific node will also be O(n). 
  - Because of the lack of organizational structure in a Binary Tree, the worst case for most operations will involve traversing the entire tree.
  - If we assume that a tree has n nodes, then in the worst case we will have to look at n items, hence the O(n) complexity.
  - The Big O space complexity for a node insertion using breadth first insertion will be O(w), where w is the largest width of the tree.
  - For example, in the above tree, w is 4.
  - A “perfect” binary tree is one where every non-leaf node has exactly two children. 
  - The maximum width for a perfect binary tree, is 2^(h-1), where h is the height of the tree. 
  - Height can be calculated as log n, where n is the number of nodes.
- __Binary Search Trees__:
  - A Binary Search Tree (BST) is a type of tree that does have some structure attached to it.
  - In a BST, nodes are organized in a manner where all values that are smaller than the root are placed to the left, and all values that are larger than the root are placed to the right.
  - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/BST1.PNG)
- __Searching a BST__:
  - Searching a BST can be done quickly, because all you do is compare the node you are searching for against the root of the tree or sub-tree. 
  - If the value is smaller, you only traverse the left side.
  - If the value is larger, you only traverse the right side.
  - ![img](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-15/resources/images/BST2.PNG)
  - __Big O__:
    - The Big O time complexity of a Binary Search Tree’s insertion and search operations is O(h), or O(height).
    - In the worst case, we will have to search all the way down to a leaf, which will require searching through as many nodes as the tree is tall. 
    - In a balanced (or “perfect”) tree, the height of the tree is log(n). In an unbalanced tree, the worst case height of the tree is n.
    - The Big O space complexity of a BST search would be O(1). During a search, we are not allocating any additional space.
