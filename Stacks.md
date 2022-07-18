# Stacks
## Introduction
A stack in programming is a data structure that has the characteristic of that any information can be added, however the only information that can be removed is the last piece added to a stack. Think of it like a shopping cart. When you are shopping, you put in food as you see it go by. However, when you go to checkout, while pulling it out of the cart you can only pull out whatever is on top first, and you need to work your way towards the bottom of the cart. 
## Common Operations
### Setting up a Stack in Python
In python, we do not have a stack in the true sense of the word. The closest thing we have is a list that we can use the common operations on. The reason why a list will be able to work just as well is because as long as we only use the common operations on the list, and avoid doing anything "stack illegal" with the list, most basic data structures can be turned into a stack. The biggest difference is that we have to avoid iterating through this list due to the fact that it is technically not supposed to be used as a list. 
```
stack = []
```
### Push()
The Push is the operation used to add new information to a stack. With the stack data structure, Every piece of information we add will always be at the end of our list. In python, the way we do a push operation is:
```
stack = []
stack.push(value)
print(stack)
```
### Pop()
The pop operation is how we remove information from a stack. Using the push operation, it will only remove information from the end of the List. There is no way in a proper stack to remove information from either the beginning, or anywhere in the middle of the stack. This means that if we want to get any information from anywhere not at the end of the list, we would have to pull everything after it out, grab that piece of data, and then add everything back in. In a stack, there is no operation known as "contains", therefore this task becomes incrediby ineffcicent. Only use a stack when you know that you are going to follow the LIFO rule (Last in, First out). In the example below, pretend we have a list of workers in the order they are hired. If our company needs to lay people off, ideally it should be laying off whoever is the employee who has been there the least amount of time. This is a perfect opportunity to use the Pop functionality. The code for this looks like:
```
Workers = ["John", "Suzy", "Paul", "Ruby"]
fired_worker = Workers.pop()
print(fired_workers) #"Ruby"
print(Workers) #["John", "Suzy", "Paul"]
```
In python, you do not need to store the popped value in a variable, on the second line we could just have easily put: `Workers.pop()` instead of `fired_worker = Workers.pop()`. It doesn't matter which one you use, however be aware that if you are actively editing a data file, once you pop a worker and the code finishes running, there is no way to get that information back without backups.
### Size()
The Size Functionality is one of the most common operations across any data structure in any language. The size operation will allow us to know how many elements we have in our stack. In the example we used above with considering lay-offs for a company, we could use this size operation in order to figure out how much money we are losing due to too many employees vs how much money each employee is pulling in. In order to get the length of any list in python, we use `len(list)`, and that is what we will use to make this program below:
```
Workers = ["John", "Suzy", "Paul", "Ruby"]
Money_per_hour = 20
Hours_per_week = 40

Total_Money_Spent = len(Workers) * (Money_per_hour * Hours_per_week)
```
In this example, we are assuming that everyone has the same pay check and the same amount of hours. this may not be true in all circumstances, but if these numbers are averaged out it will at least give us an estimate. In this example, `len(Workers)` will return that we have a staff of 4 members in order to do our calculations on. 
### empty()
Our Final Example is probably the most basic operation that can be done on any data structure: empty. The empty operation is used to determain if there are any 
## Big O Notation
|Common Stack Operation|Performance|
|--------------------|-----------|
|Push()|O(1)|
|pop()|O(1)|
|size()|O(1)|
|empty()|O(1)|
## Example
Explanation
```
code
```
## Problem to Solve
Problem Defintion
## Example Solution
```
code
```
## II. [Stacks]()
* Introduction
* Order of Insertions and removal
* Common Operations (Push, Pop, size, empty)
* Example
* Problem to Solve