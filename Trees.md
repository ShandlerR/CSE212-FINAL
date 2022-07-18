# Trees in Python
## Introduction
Trees are data strctures that allow us to organize information that will stay in a consistent order from the top of the tree to the bottom of the tree, and at any sub point. A tree is like a linked list where the only way to access information on level 2 is to go through the node on level 1. However, A tree differs by the fact that there can be multiple nodes on level two that connect to a single node on level 1. 
![binary Tree](/CSE212-FINAL/Pictures/treelevels.png)
As you can see, in order to access Either Node B or C, we would need to first go through node A. This is known as a Binary Tree, and it is the most basic of all the trees.  Depending on the level of complexity we choose and how we organize our data, we can use this structure in order to make our lookup and storage efficency incredibly low.
## Root, leaf, Parent, Child, Subtree
As stated above, trees are much like linked list where they purely rely on nodes. The "Level 1" Node is known as the root Node. the root node is the top of the tree, and is the point where all information must go through (and ususally be compared to) in order to get deeper into the tree. In most trees, this node will define the basic organization of where data will go. 
<br>

Next We will start talking about Parent and child nodes. Parent nodes are the next level up node that the current node belongs to. Using the example above, The parent of Node B and C would be Node A. The parent of Node D and E would be node B, and so on. A Child Node is the next level down that the current node can see. The child Node of A is B and C, and the Child Node of B is both D and E. Technically, with this data structure Nodes D and E have no way of knowing nodes F and G exist, the only way to access Nodes F and G would be to go through Node A > Node C > Node F/G. <br>

Finally, the last two components of a basic tree structure are Leaf, and subtrees. A Leaf Node is the opposite of a Root node. Where a root node is defined by being the top level of the tree that every piece of information must pass through, the leaf node is any node at the bottom of a tree that does not have any more nodes connecting to it. Using the example above, nodes D, E, F, G are child nodes. Let's say that we added a new node called Node I, and we added that to node D. Node D would no longer be considered a leaf node, and would be reaplaced by Node I. Our new leaf Nodes would be I, E, F, G. Subtrees are a bit more complicated. Subtrees are the middle nodes that are not considered The Root, or a leaf. A subtree is any tree that is not the root. In our exmaple, examples of subtrees would be subtree B and subtree C. if we are including node I in this, Node D would also be considered a subtree.
<br>

![Detailed Nodes](/CSE212-FINAL/Pictures/NodeDetail.png) 
## Binary Search Tree & Balanced Binary Searched Trees
### Binary Search Tree
The next level up from a binary Tree is a Binary Search Tree, and a Balanced Binary Search Tree.  These Two have all of the same qualities as a Binary Tree, however the only differences is that the order the information is entered into the tree matters. For a Binary Search Tree, The first piece of information is the "Root". The Second piece of information gets compared to the root, and then if it is less than the root, we put it on the left, and if it is greater than the root we put it on the right. To get a deeper understanding, let's work through some examples. Given The Following Tree, we will work through adding the following numbers into it: 1 and 27
![TreeExample1](/CSE212-FINAL/Pictures/TreeExample1.png)
To add 1, we look at 25, and compare to see if 1 is bigger than or less than 25. Since it's less than, we move to the right. We then do the same comparison on 15, and since it is smaller we go to the left again. Finally, we do the same comparison to 10, and since it is smaller we add it to the left of 10. 
<br>
To add 27, we compare it to 25, and see that it is bigger, and move to the right. We then compare it to 30, and since it is smaller we add it to the left. 
![TreeExample2](/CSE212-FINAL/Pictures/TreeExample2.png)
<br>
One thing you may have noticed is that no matter what tree or subtree you look at, the information will always stay the same. Every subtree to the left will only contain information less than the current 'root', and every subtree to the right will only contain information greather than the current root. For example, focusing on 27, it is Greater than 25, but also less than 30. Therefore it goes on right tree, but on the left side of that tree. 

### Balanced Binary Search Trees
A Balanced binary search tree is the ideal form of a binary search tree, where there are about the same amount of nodes on the left side of the tree as there are on the right side. There exists several algorithms to reorganize these trees after made. For either search tree, looking up and storing information is about O(log n) in performance, making it a very efficent way to store alot of numbers, however it does run the risk that if the first number you add is smaller or bigger than the rest of the numbers, it will create an unbalanced tree. This is where using those sorting algorithms can come into play. 
## Recursion:
In general, one of the most effective ways to program a tree is to use a method known as recursion. Recursion, as defined by google, is to solve a larger problem by solving smaller problems from it first. In the example of a tree, there is a very common way recursion is ususally used. Say we are looking for the number 1 in the tree example above. We first start at 25, and then do 3 checks. First, is this node None (Are we at the end of the tree). If so, return False because that means we have finished the tree and have not found anything. Second, is the current node's value equal to the value we are looking for? If so, return true. Third, if not, is it larger or smaller than the current value? If larger, go left, if smaller, go right. And to go left or right, we would call the same function we are inside of, but using the next node we aim for. At the end, this program will tell us whether or not we have found the number in the tree.

## Big O notation of Common Operations:
|Common BST Operation|Description|Performance|
|--------------------|-----------|-----------|
|insert(value)|insert a value into the tree|O(log n)|
|remove(value)|Remove a value for the tree|O(log n)|
|contains(value)|Determine if a value is in the tree|O(log n)|
|traverse_forward|Visit all of the objects from smallest to largest|O(n)|
|traverse_reverse|Visit all objects from largest to smallest|O(n)|
|height(node)|Determine the height of a node. If the height of the tree is needed, the root node is provided|O(n)
|size()| Return the size of the BST| O(1)|
|empty()|Returns true if the root node is empty. This can also be done by checking the size for 0.|O(1)|

## Examples
* Creating a library to organize my music using a BST
```
class BST:

    class Node:
        """
        Each node of the BST will have data and links to the 
        left and right sub-tree. 
        """

        def __init__(self, data):
            """ 
            Initialize the node to the data provided.  Initially
            the links are unknown so they are set to None.
            """
       
            self.data = data
            self.left = None
            self.right = None

    def __init__(self):
        """
        Initialize an empty BST.
        """
        self.root = None

    def insert(self, data):
        """
        Insert 'data' into the BST.  If the BST
        is empty, then set the root equal to the new 
        node.  Otherwise, use _insert to recursively
        find the location to insert.
        """
        if self.root is None:
            self.root = BST.Node(data)
        else:
            self._insert(data, self.root)  # Start at the root

    def _insert(self, data, node):
        """
        This function will look for a place to insert a node
        with 'data' inside of it.  The current sub-tree is
        represented by 'node'.  This function is intended to be
        called the first time by the insert function.
        """
        if data == node.data:
                return 0
        if data < node.data:
            # The data belongs on the left side.
            if node.left is None:
                # We found an empty spot
                node.left = BST.Node(data)
            else:
                # Need to keep looking.  Call _insert
                # recursively on the left sub-tree.
                self._insert(data, node.left)
        else:
            # The data belongs on the right side.
            if node.right is None:
                # We found an empty spot
                node.right = BST.Node(data)
            else:
                # Need to keep looking.  Call _insert
                # recursively on the right sub-tree.
                self._insert(data, node.right)

    def __contains__(self, data):
        """ 
        Checks if data is in the BST.  This function
        supports the ability to use the 'in' keyword:

        if 5 in my_bst:
            ("5 is in the bst")

        """
        return self._contains(data, self.root)  # Start at the root

    def _contains(self, data, node):
        """
        This funciton will search for a node that contains
        'data'.  The current sub-tree being search is 
        represented by 'node'.  This function is intended
        to be called the first time by the __contains__ function.
        """
        if data == node.data:
                return True
        if data < node.data:
            # The data belongs on the left side.
            if node.left is None:
                # We found an empty spot
                return False
            else:
                # Need to keep looking.  Call _insert
                # recursively on the left sub-tree.
                return self._contains(data, node.left)
        else:
            # The data belongs on the right side.
            if node.right is None:
                # We found an empty spot
                return False
            else:
                # Need to keep looking.  Call _insert
                # recursively on the right sub-tree.
                return self._contains(data, node.right)
        def __iter__(self):
        """
        Perform a forward traversal (in order traversal) starting from 
	    the root of the BST.  This is called a generator function.
        This function is called when a loop	is performed:

        for value in my_bst:
            print(value)

        """
        yield from self._traverse_forward(self.root)  # Start at the root
        
    def _traverse_forward(self, node):
        """
        Does a forward traversal (in-order traversal) through the 
        BST.  If the node that we are given (which is the current
        sub-tree) exists, then we will keep traversing on the left
        side (thus getting the smaller numbers first), then we will 
        provide the data in the current node, and finally we will 
        traverse on the right side (thus getting the larger numbers last).

        The use of the 'yield' will allow this function to support loops
        like:

        for value in my_bst:
            print(value)

        The keyword 'yield' will return the value for the 'for' loop to
	    use.  When the 'for' loop wants to get the next value, the code in
	    this function will start back up where the last 'yield' returned a 
	    value.  The keyword 'yield from' is used when our generator function
        needs to call another function for which a `yield` will be called.  
        In other words, the `yield` is delegated by the generator function
        to another function.

        This function is intended to be called the first time by 
        the __iter__ function.
        """
        if node is not None:
            yield from self._traverse_forward(node.left)
            yield node.data
            yield from self._traverse_forward(node.right)
        
    def __reversed__(self):
        """
        Perform a formward traversal (in order traversal) starting from 
        the root of the BST.  This function is called when a the 
        reversed function is called and is frequently used with a for
        loop.

        for value in reversed(my_bst):
            print(value)

        """        
        yield from self._traverse_backward(self.root)  # Start at the root
    
library = BST()
library.insert(["Fireworks", "Katy Perry"])
library.insert("Monster", "Skillet")

print(["Fireworks", "Katy Perry"] in library)
```
## Problem to Solve
having the same BST as above, how do we make it so you can still find the song, but only given the name and not the artist?

## Sample Solution:
```
class BST:

    class Node:
        """
        Each node of the BST will have data and links to the 
        left and right sub-tree. 
        """

        def __init__(self, data):
            """ 
            Initialize the node to the data provided.  Initially
            the links are unknown so they are set to None.
            """
       
            self.data = data
            self.left = None
            self.right = None

    def __init__(self):
        """
        Initialize an empty BST.
        """
        self.root = None

    def insert(self, data):
        """
        Insert 'data' into the BST.  If the BST
        is empty, then set the root equal to the new 
        node.  Otherwise, use _insert to recursively
        find the location to insert.
        """
        if self.root is None:
            self.root = BST.Node(data)
        else:
            self._insert(data, self.root)  # Start at the root

    def _insert(self, data, node):
        """
        This function will look for a place to insert a node
        with 'data' inside of it.  The current sub-tree is
        represented by 'node'.  This function is intended to be
        called the first time by the insert function.
        """
        if data == node.data:
                return 0
        if data < node.data:
            # The data belongs on the left side.
            if node.left is None:
                # We found an empty spot
                node.left = BST.Node(data)
            else:
                # Need to keep looking.  Call _insert
                # recursively on the left sub-tree.
                self._insert(data, node.left)
        else:
            # The data belongs on the right side.
            if node.right is None:
                # We found an empty spot
                node.right = BST.Node(data)
            else:
                # Need to keep looking.  Call _insert
                # recursively on the right sub-tree.
                self._insert(data, node.right)

    def __contains__(self, data):
        """ 
        Checks if data is in the BST.  This function
        supports the ability to use the 'in' keyword:

        if 5 in my_bst:
            ("5 is in the bst")

        """
        return self._contains(data, self.root)  # Start at the root

    def _contains(self, data, node):
        """
        This funciton will search for a node that contains
        'data'.  The current sub-tree being search is 
        represented by 'node'.  This function is intended
        to be called the first time by the __contains__ function.
        """
        if data == node.data:
                return True
        if data < node.data:
            # The data belongs on the left side.
            if node.left is None:
                # We found an empty spot
                return False
            else:
                # Need to keep looking.  Call _insert
                # recursively on the left sub-tree.
                return self._contains(data, node.left)
        else:
            # The data belongs on the right side.
            if node.right is None:
                # We found an empty spot
                return False
            else:
                # Need to keep looking.  Call _insert
                # recursively on the right sub-tree.
                return self._contains(data, node.right)
        def __iter__(self):
        """
        Perform a forward traversal (in order traversal) starting from 
	    the root of the BST.  This is called a generator function.
        This function is called when a loop	is performed:

        for value in my_bst:
            print(value)

        """
        yield from self._traverse_forward(self.root)  # Start at the root
        
    def _traverse_forward(self, node):
        """
        Does a forward traversal (in-order traversal) through the 
        BST.  If the node that we are given (which is the current
        sub-tree) exists, then we will keep traversing on the left
        side (thus getting the smaller numbers first), then we will 
        provide the data in the current node, and finally we will 
        traverse on the right side (thus getting the larger numbers last).

        The use of the 'yield' will allow this function to support loops
        like:

        for value in my_bst:
            print(value)

        The keyword 'yield' will return the value for the 'for' loop to
	    use.  When the 'for' loop wants to get the next value, the code in
	    this function will start back up where the last 'yield' returned a 
	    value.  The keyword 'yield from' is used when our generator function
        needs to call another function for which a `yield` will be called.  
        In other words, the `yield` is delegated by the generator function
        to another function.

        This function is intended to be called the first time by 
        the __iter__ function.
        """
        if node is not None:
            yield from self._traverse_forward(node.left)
            yield node.data
            yield from self._traverse_forward(node.right)
        
    def __reversed__(self):
        """
        Perform a formward traversal (in order traversal) starting from 
        the root of the BST.  This function is called when a the 
        reversed function is called and is frequently used with a for
        loop.

        for value in reversed(my_bst):
            print(value)

        """        
        yield from self._traverse_backward(self.root)  # Start at the root
    
library = BST()
library.insert(["Fireworks", "Katy Perry"])
library.insert("Monster", "Skillet")

for node in Library:
    if node[0] == "Fireworks":
        return True
```