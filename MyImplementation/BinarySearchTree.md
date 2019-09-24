# Binary Search Tree(BST)
They are also know as *ordered or sorted binary trees*.
### BST property
The tree additionally satisfies the binary search property, which states that the key in each node must be greater 
than or equal to any key stored in the left sub-tree, and less than or equal to any key stored in the right sub-tree.
### Time Complexity
Algorithm|Average|Worst case
---------|-------|----------
Space|O(n)|O(n)
Search|O(log(n))|O(n)
Insert|O(log(n))|O(n)
Delete|O(log(n))|O(n)

## Implementation of BST
```python
# basic building block of a tree
class Node(object):
    def __init__(self, value):
        self.value = value
        self.left = None
        self.right = None
        self.parent = None

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
* if the node is the left child of its parent, then it must be smaller than (or equal to) the parent and it must pass down the value from its parent to its right subtree to make sure none of the nodes in that subtree is greater than the parent<br/>
* if the node is the right child of its parent, then it must be larger than the parent and it must pass down the value from its parent to its left subtree to make sure none of the nodes in that subtree is lesser than the parent.<br/>

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
    def search(self, start, find_val): #output:: if found Node is returned else None
        if start == None or start.value == find_val:
            return start

        if find_val < start.value:
            return self.search(start.left, find_val)

        return self.search(start.right, find_val)
```
### Insertion
```python
    def insertNode(self, start, newNode):
        if start == None:
            start = newNode # INSERT HERE
        
        elif start.value == newNode.value:
            newNode.parent = start.parent
            pass #NO INSERT, VALUE ALREADY PRESENT
        
        elif start.value > newNode: #INSERT TO LEFT SUB-TREE
            newNode.parent = start
            self.insertNode(start.left, newNode)
        
        else: #INSERT TO RIGHT SUB-TREE
            newNode.parent = start
            self.insertNode(start.right, newNode)
        return
```
### Deletion
Threre are 3 cases for deletion:<br/>
1. Deleting a node with no children: simply remove the node from the tree.<br/>
2. Deleting a node with one child: remove the node and replace it with its child.<br/>
3. Deleting a node with two children: call the node to be deleted D. Do not delete D. Instead, choose either its in-order predecessor node *(left sub-tree right-most child)* or its in-order successor node *(right sub-tree left-most child)* as replacement node E (in below figure). Copy the values of E to D If E does not have a child simply remove E from its previous parent G. If E has a child, say F, it is a right child. Replace E with F at E's parent.

![Figure for Deletion](https://upload.wikimedia.org/wikipedia/commons/thumb/3/36/AVL-tree-delete.svg/640px-AVL-tree-delete.svg.png)
<br/>Source:: [Wikipedia](https://en.wikipedia.org/wiki/Binary_search_tree#Deletion)
```python
    def findLeftMost(self, start):
        current = start
        while current != None and current.left != None:
            current = current.left
        
        return current
    
    def replaceParentNode(self, start, child):
        if start.parent: # if not root node
            if start == start.parent.left_child: # check if current node is the left child of its parent
                start.parent.left_child = new_value
            
            else: # else current node is the right child of its parent
                start.parent.right_child = new_value
        
        if child: # change the parent of the child node to current node's parent
           child.parent = start.parent
        
        return
    
    def delete(self, start, value):
        if start != None:
            if start.value == value: #Found node
                if start.left != None and start.right != None: #case 3: Node with 2 child
                    successor = self.findLeftMost(start.right) # find successor of the right child to replace
                    start.value = successor.value # replace node value
                    self.delete(successor, successor.value) # delete successor 
                
                elif start.left: #case 2: Node with 1 child (left child here)
                    self.replaceParentNode(start, start.left)
                
                elif start.right: #case 2: Node with 1 child (right child here)
                    self.replaceParentNode(start, start.left)
                
                else: #case 1: Node with 0 children
                    self.replaceParentNode(start, None)
            
            elif value < start.value: #Search left subtree
                self.delete(start.left, value)
            
            elif value > start.value: #Search right subtree
                self.delete(start.right, value)
        return
``` 
