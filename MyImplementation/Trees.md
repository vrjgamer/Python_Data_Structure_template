# Trees
### Properties of a tree
1. Tree should be completely connected, meaning there should be a path from root to reach every node in a tree
2. Tree should not have cycles

### General terminologies in a tree
Parent, Child, Leaf, Ancestor, Descendant, Level, Edges, Path, Height, Depth

### Traversals 
#### BFS : Breath First Search
It starts at the tree root (or some arbitrary node of a graph, sometimes referred to as a 'search key'[1]), 
and explores all of the neighbor nodes at the present depth prior to moving on to the nodes at the next depth level.

#### DFS : Depth First Search
The algorithm starts at the root node (selecting some arbitrary node as the root node in the case of a graph) 
and explores as far as possible along each branch before backtracking.<br/>
Types of DFS traversal<br/>
A) Inorder<br/>
    1 Check if the current node is empty or null.<br/>
    2 Traverse the left subtree by recursively calling the in-order function.<br/>
    3 Display the data part of the root (or current node).<br/>
    4 Traverse the right subtree by recursively calling the in-order function.<br/>

B) Pre-order<br/>
    1 Check if the current node is empty or null.<br/>
    2 Display the data part of the root (or current node).<br/>
    3 Traverse the left subtree by recursively calling the pre-order function.<br/>
    4 Traverse the right subtree by recursively calling the pre-order function.<br/>

C) Post-order<br/>
    1 Check if the current node is empty or null.<br/>
    2 Traverse the left subtree by recursively calling the post-order function.<br/>
    3 Traverse the right subtree by recursively calling the post-order function.<br/>
    4 Display the data part of the root (or current node).<br/>
