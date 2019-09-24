# Binary Search Tree(BST)
They are also know as *ordered or sorted binary trees*.
### BST property
The tree additionally satisfies the binary search property, which states that the key in each node must be greater 
than or equal to any key stored in the left sub-tree, and less than or equal to any key stored in the right sub-tree.

## Implementation of BST
```python
# basic building block of a tree
class Node(object):
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None

class BinaryTree(object):
    def __init__(self, root):
        self.root = Node(root)
```
### Printing tree
#### Pre-order printing
```python
    def pre_order_print(self, start, result):
      #CHECK FOR LEAF NODE
      if start == None:
        return result
      
      #PRINT AS SOON AS YOU VISIT A NODE
      result += str(start.value) + "-"
      
      #VISIT LEFT SUB-TREE
      result = self.pre_order_print(start.left, result)
      
      #VISIT RIGHT SUB-TREE
      result = self.pre_order_print(start.left, result)
      
      return result
```
#### In-order printing
```python
    def in_order_print(self, start, result):
      #CHECK FOR LEAF NODE
      if start == None:
        return result
      
      #VISIT LEFT SUB-TREE
      result = self.in_order_print(start.left, result)
      
      #PRINT AFTER VISITING ENTIRE LEFT SUB-TREE
      result += str(start.value) + "-"
      
      #VISIT RIGHT SUB-TREE
      result = self.in_order_print(start.left, result)
      
      return result
```
#### post-order printing
```python
    def post_order_print(self, start, result):
      #CHECK FOR LEAF NODE
      if start == None:
        return result
      
      #VISIT LEFT SUB-TREE
      result = self.post_order_print(start.left, result)
      
      #VISIT RIGHT SUB-TREE
      result = self.post_order_print(start.left, result)
      
      #PRINT AFTER VISITING BOTH LEFT & RIGHT SUB-TREE
      result += str(start.value) + "-"
      
      return result
```
### Verifying BST
Verify if the entire tree follows the BST property, so check<br/>

-> if the node is the left child of its parent, then it must be smaller than (or equal to) the parent and it must pass down the value from its parent to its right subtree to make sure none of the nodes in that subtree is greater than the parent<br/>

-> if the node is the right child of its parent, then it must be larger than the parent and it must pass down the value from its parent to its left subtree to make sure none of the nodes in that subtree is lesser than the parent.<br/>

*(You basically send in the range of value down the subtree to check on)*

```python
  def isBST(self, start, minVal, maxVal):
    #CHECK IF THE NODE EXISTS
    if start == None:
      return true
    #CHECKK IF NODEE VALUE IS IN THE SUB-TREE RANGE
    if start.value < minVal or start.value > maxVal:
      return false
    
    # for distinct values use 
    # self.isBST(start.left, minVal, start.value - 1) and self.isBST(start.right, start.value + 1, maxValue)
    
    # use below if duplicates are allowled
    return self.isBST(start.left, minVal, start.value) and self.isBST(start.right, start.value, maxValue)
    
# to call method use isBST(root, sys.maxint, (-sys.maxint - 1)) # pass max and min integer values
```
### Searching
```python
    def search(self, start, find_val): #output if found Node is returned else None
        if start == None or start.value == find_val:
            return start

        if find_val < start.value:
            return self.search(start.left, find_val)

        return self.search(start.right, find_val)
```

