### Binary tree completeness

Implement a method that checks whether a binary tree is complete. This can be done (for example) by adapting the Breadth-First Search algorithm.

The binary tree can have at most two children, which are both again a binary tree (or null if the child does not exist).

The class BinaryTree has the following methods:
```java
class BinaryTree {
  // Constructor with no children
  BinaryTree(int key);

  // Constructor with two children
  BinaryTree(int key, BinaryTree left, BinaryTree right);

  // Returns the key of the root of this tree.
  int getKey();

  // Returns the left child of this tree iff hasLeft(v) is true, else null.
  BinaryTree getLeft();

  // Returns the right child of this tree iff hasRight(v) is true, else null.
  BinaryTree getRight();

  // Returns true iff this tree has a left child.
  boolean hasLeft();

  // Returns true iff this tree has a right child.
  boolean hasRight();

  // Set the new left child of this tree.
  void setLeft(BinaryTree child);

  // Set the new right child of this tree.
  void setRight(BinaryTree child);
}
```
```java
import java.util.*;

class Solution {
  /**
   * Computes whether the BinaryTree is complete.
   *
   * @param tree
   *     the BinaryTree to check.
   * @return true iff the BinaryTree is complete, else false.
   */
  public static boolean isTreeComplete(BinaryTree tree) {
    if(tree == null) return true;
    Queue<BinaryTree> q = new LinkedList<BinaryTree>();
    q.add(tree);
    boolean check = false; //checking if last level has all nodes
    while(!q.isEmpty()){
      BinaryTree t = q.poll();
      
      if(!t.hasLeft() && t.hasRight()) return false;
      
      if (check && (t.hasLeft() || t.hasRight())) return false;
          
      if(t.hasLeft()) q.add(t.getLeft());
      else check=true;
      
      if(t.hasRight()) q.add(t.getRight());
      else check = true;
      
    }
    return true;
    
    
  }
}
```
