# Java Data Structures CheatSheet - Tree
A tree is a non linear data structure used to organize data using a parent-child relationship. It is consisted of nodes, where each node can contains one or more child nodes. The topmost node is called the root. The bottom nodes are the leafs.

## Types of trees
- Binary search tree (BST)   
  BSTs are trees where each node contains at most two childrens (binary) and each node attends to the BST property: $leftnode < root < rightnode$. This way is guaranteed that the entire left subtree only contains nodes smaller than the root and the right subtree only contains nodes bigger than the root.

## Types of traversals
- Inorder $Left - Root - Right$      
  Commonly used with BSTs. Checks the entire left tree, the current node and then the entire right tree. Creates a ordered list of all the nodes of the tree (for BSTs). 
- Preorder $Root - Left - Right$   
  Start by visiting the root, then it vists the entire left subtree and after that the entire right subtree. Useful to copy a tree.
- Postorder $Left - Right - Root$   
  Start by visiting the left and right subtrees. Only after that, the current node is visited. Useful to deleting the tree (first deletes its chidreens and after deletes the root).