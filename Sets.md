# Sets
## Introduction
Sets are a data structure in python that are very similar to lists. They allow us to store an unlimited amount of data in them, and allow us to lookup this information and pull it out as we need. The difference with a  set is that it does not allow duplicates like lists do, it does not keep information in order, and every piece of information has a specific place for it when the set is created. This is done through the act of hasing.
## Hashing
An Easy way to imagine a hash is as an equation for how we will store our information in our list. The attributes of a Sets is that they have incredibly low lookup and upload time. In order to get this performance, we could make our equation something like `index(n) = n*2`. This is a very basic example of the idea behind a hash. Every piece of data we store in our list now has a home. If we want to store the number 20 in our list, we would store it at index 40. 
</br></br>
A problem that you may notice that we will face with a system like this is that what happens as our numbers gets larger, and we get more of them? Storing a number like 2 wouldn't be so bad since then we just need to put it at index 4, however what happens if we want to store all the numbers from 1 to 25214? By the end of it, our index is beginning to become unwieldy to manage. The way to solve this would then to be to instead of just using our n in our equation, we could shorten this number by doing n % 10. this will allow us to use much less memory for our program, while still getting the great lookup time and upload time (since everything still has it's place.).
## Conficts
With the current set, what happens when we have two pieces of data that would be put in the same index? In theory, since we are still storing the same amount of data, but in a smaller space, this is bound to become a problem at some point. One of the best methods known of dealing with this issue is the use an operation known as `chaining`. what chaining is, is that at any point when we have two pieces of data that should in theory go in the same spot, we create a list at that point. That way, when it comes to lookup it still has the same position we theorize it does, just now there are two things at that position. One risk we can end up running into, however, is that if we end up having too many of these conflicts, our performance will suffer. The best way to deal with this problem is to omcrease the size of our list. It will give us great lookup time, and still be less painful on memory than using an O(n) solution like a list. 

## Big O Notation of Common Operations
|Common BST Operation|Description|Python Code|Performance|
|--------------------|-----------|-----------|-----------|
|add(value)|Adds "value" to the set|my_set.add(value)|O(1)|
|remove(value)|Remove a value for the Set|my_set.remove(value)|O(1)|
|member(value)|Determine if a value is in the Set|if value in my_set:|O(1)|
|size()| Return the number of elements in the set|length = len(my_set)|O(1)|
## Example
Maximum and Minimum Value
Say we have a program that is record the speed of a car during a race. We then take all of this information and put it into a set. We want to code a program that will tell us what the fastest and slowest speed of the car is. This program can look like:
```
speeds_mph = {100,50,10,200,...}
print(max(speeds_mph))
print(min(speeds_mph))
```
## Problem to Solve
Say we have a list of 10 numbers. we want a program that will check if our list contains duplicates. Write a program that will utilize a set in order to find out whether or not our list contains duplicate numbers. HINT: Sets can only hold unique values in them.
## Sample Solution
```
numbers = [10, 5, 10, 2, 4, 8, 9, 1, 3, 7]
numbers_set = set(numbers)
if len(numbers_set) != len(numbers):
    print("Numbers contains duplicates")
else:
    print("Numbers contains no duplicates")
``` 