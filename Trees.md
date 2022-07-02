# Trees in Python
## Introduction
Trees are data strctures that allow us to organize information that will stay in a consistent order from the top of the tree to the bottom of the tree, and at any sub point. A tree is like a linked list where the only way to access information on level 2 is to go through the node on level 1. However, A tree differs by the fact that there can be multiple nodes on level two that connect to a single node on level 1. 
![binary Tree](/Pictures/treelevels.png)
As you can see, in order to access Either Node B or C, we would need to first go through node A. This is known as a Binary Tree, and it is the most basic of all the trees.  Depending on the level of complexity we choose and how we organize our data, we can use this structure in order to make our lookup and storage efficency incredibly low.
## Root, leaf, Parent, Child, Subtree
As stated above, trees are much like linked list where they purely rely on nodes. The "Level 1" Node is known as the root Node. the root node is the top of the tree, and is the point where all information must go through (and ususally be compared to) in order to get deeper into the tree. In most trees, this node will define the basic organization of where data will go. 
<br>

Next We will start talking about Parent and child nodes. Parent nodes are the next level up node that the current node belongs to. Using the example above, The parent of Node B and C would be Node A. The parent of Node D and E would be node B, and so on. A Child Node is the next level down that the current node can see. The child Node of A is B and C, and the Child Node of B is both D and E. Technically, with this data structure Nodes D and E have no way of knowing nodes F and G exist, the only way to access Nodes F and G would be to go through Node A > Node C > Node F/G. <br>

Finally, the last two components of a basic tree structure are Leaf, and subtrees. A Leaf Node is the opposite of a Root node. Where a root node is defined by being the top level of the tree that every piece of information must pass through, the leaf node is any node at the bottom of a tree that does not have any more nodes connecting to it. Using the example above, nodes D, E, F, G are child nodes. Let's say that we added a new node called Node I, and we added that to node D. Node D would no longer be considered a leaf node, and would be reaplaced by Node I. Our new leaf Nodes would be I, E, F, G. Subtrees are a bit more complicated. Subtrees are the middle nodes that are not considered The Root, or a leaf. A subtree is any tree that is not the root. In our exmaple, examples of subtrees would be subtree B and subtree C. if we are including node I in this, Node D would also be considered a subtree.
<br>

![Detailed Nodes](/Pictures/NodeDetail.png) 
## Binary Search Tree & Balanced Binary Searched Trees
## Binary Search Tree
The next level up from a binary Tree is a Binary Search Tree, and a Balanced Binary Search Tree.  These Two have all of the same qualities as a Binary Tree, however the only differences is that the order the information is entered into the tree matters. For a Binary Search Tree, The first piece of information is the "Root". The Second piece of information gets compared to the root, and then if it is less than the root, we put it on the left, and if it is greater than the root we put it on the right. To get a deeper understanding, let's work through some examples. Given The Following Tree, we will work through adding the following numbers into it: 1 and 27
![TreeExample1](/Pictures/TreeExample1.png)
To add 1, we look at 25, and compare to see if 1 is bigger than or less than 25. Since it's less than, we move to the right. We then do the same comparison on 15, and since it is smaller we go to the left again. Finally, we do the same comparison to 10, and since it is smaller we add it to the left of 10. 
<br>
To add 27, we compare it to 25, and see that it is bigger, and move to the right. We then compare it to 30, and since it is smaller we add it to the left. 
![TreeExample2](/Pictures/TreeExample2.png)
<br>
One thing you may have noticed is that no matter what tree or subtree you look at, the information will always stay the same. Every subtree to the left will only contain information less than the current 'root', and every subtree to the right will only contain information greather than the current root. For example, focusing on 27, it is Greater than 25, but also less than 30. Therefore it goes on right tree, but on the left side of that tree. 

### Balanced Binary Search Trees
A Balanced binary search tree is the ideal form of a binary search tree, where there are about the same amount of nodes on the left side of the tree as there are on the right side. There exists several algorithms to reorganize these trees after made. For either search tree, looking up and storing information is about O(log n) in performance, making it a very efficent way to store alot of numbers, however it does run the risk that if the first number you add is smaller or bigger than the rest of the numbers, it will create an unbalanced tree. This is where using those sorting algorithms can come into play. 


but still have O(log n) in lookup and storage. This is only in a balanced search tree, hwoever.
* Binary Search Tree, Binary Tree, Balanced Binary Search Tree
## Example
## Problem to Solve
