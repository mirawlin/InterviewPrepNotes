#interviewPrep

## Algorithms

![[Pasted image 20220110211134.png]]

### Recursion

Algorithms + Data Structures = Programs

Class {} + Function() = Programs


**Recursion**
when you define something in terms of itself --> a function that refers to itself

Recursion is good for tasks that have repeated subtasks to do



**StackOverflow**

![[Pasted image 20220110212748.png]]

recursive functions --> in the browser, there is a call stack that tracks the functions being called
if it is an endless loop --> nothing in the stack gets removed and the stack runs out of memory --> stack overflow

stacks hold onto memory calls

stack overflow occurs when we have no way of stopping the recursive function


**Anatomy of Recursive Functions**

Every recursive function needs a base case or a stop function 

2 paths:
- recursive case --> call the function again and run
- base case --> stop calling the function 

Need to always return --> so that the result can bubble up once it reaches the base case

usually there are 2 returns

### Recursive vs Iterative

Anything you do with recursion can be done iteratively

recursion can help simplify code --> less repetition and sometime cleaner/more readable
but its not always the best option

Cons --> has large stack --> might get stack overflow or will take up a lot of memory


**Tail call Optimisation** --> allows recursions to be called without increasing the call stack

there are certain ways to write recurions so they are more memory efficient 

### When to use Recursion
- useful for complicated problems eg traversal / searching through trees or graphs / Sorting 

**Rules**
- If using a Tree or converting something to a tree consider recursion

3 things during interview questions that might trigger a recursion:
	1. problem can be divided into a number of subproblems that are smaller instances of the same problem
	2. Each instance of the subproblem is identical in nature
	3. The solutions of each subproblem can be combined to solve the problem at hand
	
Divide and conquer using Recursion


Pros and cons of recursion 

- code more readable, can make solving certain problems easier
	- e.g. merge sort, quick sort, tree traversal, graph traversal
- need to be careful with space complexity


## Sorting

Sorting is not a big deal if its a small input data

When inputs are extremely large --> can cost a lot to perform the operation

Bubble sort
Insertion Sort
Selection Sort
Merge Sort
Quick Sort

**The issue with the inbuilt sort()**
- need to know how it is implemented/what it is doing under the hood to know what the outcome is
	- e.g. in javascript --> if trying to sort integers, they are converted to strings and it takes the first character and it takes the unicode value of the number --> hence the numbers wont be sorted as expected
- time and space complexity of the sort cannot be guaranteed --> depends on the implementation

https://www.toptal.com/developers/sorting-algorithms


### Bubble Sort
basic sorting algorithm 

first 3 more basic
last 2 more complex

![[Pasted image 20220115174810.png]]


bubble up the highest number 

one of the simplest sort --> also one of the most inefficient
O(n^2) - time complexity
O(1) - Space complexity


### Selection Sort

O(n^2) - time complexity
O(1) - space complexity

scans through the list to find the smallest item --> moves it to the top and goes through the whole list again

![[Pasted image 20220116110210.png]]


### Insertion Sort

Not the most efficent --> but there are cases when they are extremely fast

Useful for when you're sure that the list is almost sorted

best case scenario --> O(n) when list is almost sorted
worst case scenario --> O(n^2)

performs well with small datasets


### Merge Sort

**O(n log n)** - time complexity
O(n) - space complexity

Merge sort and quick sort --> divide and conquer --> gives log n advantage

one of the most efficient sorting algorithms



### Quick Sort

divide and conquer algorithm
Time complexity
best case O(n log n)
worst case O(n^2)

Space complexity O(n)

pivoting technique --> breaks list into smaller lists and use pivoting technique until sorted

randomly selects pivot point - compares every item in the list --> if it is smaller than pivot number its on its left , if it is bigger it goes to its right

we then have the position of the pivot number --> list is split into 2 --> left and right of pivot number and process is repeated

if you dont pick a good pivot (eg its the smallest or the largest item) --> then it could be O(n^2) --> you're not splitting the list in half

usually the fastest on average (or merge sort)


### Which sort to use?

**Insertion sort** --> used for only a few items, or if its mostly sorted, list is small
	- it uses little space (O(1)), and is easy to implement in code
	
Bubble Sort --> probably never --> not very efficient

Selection Sort --> probably never --> not very efficient

Merge Sort --> Fast , all cases are O(n log n) --> if you're worried about worst case scenario use Merge Sort
But if sorting in memory on local machine --> O(n) --> expensive Space Complexity
if its suitable for external sorting eg not in memory --> then merge sort is fine sine we dont need to worry about space complexity

Quick Sort --> More popular sorting algorithsm --> need to be careful of worst case
Space complexity is good

Heap Sort --> Theoretically looks better than Quicksort and Merge sort (good time and space complexity) --> but on average is slower (Quick sort doesnt do unneccessary swapping, where as Heap sort will still swap numbers that are already ordered)

### Radix Sort + Counting Sort

Non comparison sorts 
Counting Sort
Radix sort

These Non comparison sorts uses the number's binary --> only works for Integer numbers (within a particular range)

The others are called Comparison Sort 


Exercise
1 - Insert +
2 - merge x --> radix or counting
3 - insert x --> quick sort
4 - quick x --> merge (dont want worst case and dont need memory)
5 - insert +
6 - merge x --> quick 
7 - merge or quick
8 - bubble



Quick sort --> when average case performance matters more than worse case
merge sort --> performs equall well in all cases --> space complexity high 

![[Pasted image 20220120122159.png]]



## Searching --> BFS + DFS
Breadth first sort and depth first sort

Types of Searching / Traversal
- Linear Search
- Binary Search
- Depth First Search
- Breadth First Search


### Linear Search
Linear search / Sequential Search --> finding a value in a list

iterate through all items in list until found or until you reach end of list 

O(n)


### Binary Search
In a sorted list --> take middle item, compare it to the item we're looking for, if its less than what we are looking for we can remove everything in the list to its left (works the same for if its greater but remove the right side)

If data is sorted --> can look at it like a binary search tree

Storing data in tree is more efficient than in an array

O(log n)


### Graph + Tree traversals

Traversal --> visit every node of a tree / graph 

O(n)


### BFS - Breadth First Search
Searching or traversing through a tree

Start with root node --> then move left to right to the next level --> continue until you find the node you look for or until the tree ends

uses additional memory --> need to track all the child nodes of all the nodes of a given level


### DFS - Depth First Search
follows one branch of a tree down as many levels until there are no more nodes
Goes up to the neareast ancestor to see if there are any missing unexplored children and continues

Uses less memory compared to BFS --> dont need to store and track all teh child nodes at a given level 

eg.
 ```
      9
	4   20
  1  6 15  170
 ```
 
 BFS [ 9, 4, 20, 1, 6, 15, 170]
 DFS [ 9, 4, 1, 6, 20, 15, 170]
 
 
 ### BFS vs DFS
 O(n)
 
 Trying to go through the tree without repeating nodes
 Order matters in BFS and DFS

#### BFS
 BFS --> Good for Finding shortest path between a starting point and any other reachable node
 starts with root node --> then search closest nodes then further and further away
 
 Cons --> More memory required
 
 If you know that the target node is likely towards the top of the tree BFS is better as it searches the closes nodes first
 
 ![[Pasted image 20220120152644.png]]
 
 #### DFS
 
 If you know the target node is likely towards the lower level of a tree - DFS is possibly better in this scenario 
 
 DFS --> Asks the question --> Does the path exist?
 uses less memory
 
 Cons --> can be slow
 
 ![[Pasted image 20220120154510.png]]
 
 
 Exercises
 1. If you know a solution is not far from the root of the tree?
 BFS
 
 2. If the tree is very deep and solutions are rare?
  BFS (DFS will take too long, BFS will be faster, but there may be memory concerns)
  
 3. If the tree is very wide?
  DFS (BFS will need too much memory)
  
 4. If Solutions are frequent but located deep in the tree?
 DFS
 
 5. Determining whether a path exists between 2 nodes?
  DFS
  
 6. Finding shortest Path
  BFS
  
  
  **DFS**
  3 ways of returning the DFS
  Inorder --> binary search tree --> returns values in order
  preorder --> parent node --> left --> right --> useful for recreating a tree
  postorder --> go all the way down --> get the bottom nodes then traverse up to the parent
  
   ```
      9
	4   20
  1  6 15  170
 ```
 Inorder : [ 1, 4, 6, 9, 15, 20, 170]
 preorder: [ 9, 4, 1, 6, 20, 15, 170]
 postOrder: [ 1, 6, 4, 15, 170, 20, 9]
  
  ![[Pasted image 20220120171806.png]]
  
  ### BFS/DFS with Graphs
  
  BFS --> can see closes relationships in graphs
  eg what are the most related items
  
  
  ![[Pasted image 20220120175746.png]]
  
  
  **BFS**
  - determines the shortest path between any node

can help convert a graph to a tree

used in recommendation engines, P2P networks, google maps


**DFS**


### Dijkstra + Bellmen Ford Algorithms

good for finding shortest path 

BFS --> assumes that each node is equal in weight 
doesnt take into consideration the weight of an edge

eg. Google map traffic 

Dikjstra / Bellman Ford --> good for shortest path for a weighted graph


Bellman --> can accomodate negative weights
not the most efficient
O(n^2)

Dikstra --> a bit faster and efficient but cannot accomodate negative weights


## Dynamic Programming
**Optimisation Technique** --> Caching

If you have something you can cache --> can use dynamic programming

Dynamic programming --> a way to solve problems by breaking it down into a collection of problems 
after solving the problem once --> save the solution incase the problem comes up again


**Memoisation** - Caching
Caching --> a way to store values so you can use it later on


Dynamic programing --> divide and conquer + memoisation


![[Pasted image 20220121184710.png]]
