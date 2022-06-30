
# Data Structures and Algorithms

## BIG O

### What is good code?
- readable
- scalable --> Big O notation allows us to measure the idea of scalable code 

BigO notation is the language we use to compare how long an algorithm takes to run
- we can compare different algorithms using BigO and say which one is better when it comes to scale regardless of computer differences 

![../Images/Pasted image 20211226162233.png]

Big O --> when we get bigger and bigger with input, how much does the algorithm or function slow down --> algorithmic efficiency

look at number of steps/operations it takes to perform the function


### O(n) -Fair
O(n) --> Linear time
most common


### O(1) - Excellent
O(1) --> Constant Time
no matter what number of boxes we have we are only getting one item
- doesnt matter if it O(100) --> if it is constant we call it O(1)

e.g.
``` Kotlin
fun compressFirstBox(boxes: Array) {
	println(boxes[0])
}
```

### Simplifying Big O
4 rules to simplify the Big O notation

1. Worst Case
2. Remove Constants
3. Different terms for inputs
4. Drop Non Dominants

#### Worst Case
Big O --> concerned about the worst case 
eg. if you have a for loop and the item you're looking for is the 2nd item, Big O notation will still consider it as O(n) as it could be that your value is at the end of the list


#### Remove Constants
We dont care about the constants --> we are only concerned about the scalability of a function.
Constants are insignificant when we scale the algorithm

eg. O(2 + n/2 + 100) --> O(n)
O(2n) --> O(n)

The above algorithms are still linear --> therefore O(n)

#### Different Terms for Inputs
![[Pasted image 20211226172929.png]]

If there are 2 input values in a function and there are 2 separate for loops--> need to consider both of them as they are independent.

eg. first array might have 100 values, 2nd array might have 2 
If loop is one after the other --> we add
**O(a + b)**

If the for loop is nested --> we multiply
**O(a * b)**

### O(n^2) --> Horrible

nested loops --> multiply
O(n * n) --> O(n^2) --> Quadratic Time

if you have 3 nested for loops --> O(n^3)


### Drop Non Dominant

If Big O of function is: 
O(n + n^2) --> the n^2 is more important/significant than n
O(n^2)


### Big O --> Summary
O(1) -> Constant - no loops
O(log n) --> Logarithmic --> usually searching algorithms have log(n) if they are sorted (Binary Search) (Not Hash Map)
O(n) --> Linear --> for loops, while loops
O(n* log(n)) --> Log linear --> most sorting operations usually
O(n^2) --> Quadratic --> every element in a collection needs to be compared to every other element --> 2 nested loops
O(2^n) --> Exponential --> recursive algorithm that solves a problem of size N
O(n!) --> adding a loop for every element

### O(n!) --> Horrible --> Factorial 
Factorial --> adding a loop for every element 
Wont see often

### Scalability
1. Speed/Time
2. Memory

### 3 Pillars of Code
1. Readable
2. Speed (Time complexity (big O notation))
3. Memory - memory usage of code (Space Complexity (big O notation))

### Space Complexity
- Heap --> stores variables
- Stack --> keep track of function calls


what causes space complexity:
- Variables
- Data Structures
- Function Call
- Allocations


## Interview Data Structures

### Data Structures 
- Arrays
- Stacks
- Queues
- Linked Lists
- Trees
- Tries
- Graphs
- Hash Tables

### Algorithms
- Sorting 
- Dynamic Programming
- BFS + DFS (Searching)
- Recursion



for nested for loops --> can use hash tables to speed things up

### Data Structure
Data Structure = collection of values
algorithms --> steps or processes we put into place to manipulate these collections of values

Data Structure  + algorithms = programs

Data structure --> collection of values
values can have relationships and can have functions apply to them

each data structure is specialised for its own thing


1. How to build one
2. How to use it --> important

CPU
RAM --> non persistant --> fast
Storage --> persistant --> slow

Operations:
- Insertion
- Deletion
- Traversal
- Access
- Searching
- Sorting


### Arrays

- lists --> organises data sequentially
- simplest and most widely used data structure
- stored in contiguous memory (in order) --> smallest foot print and least amount of rules

Lookup (access) --> O(1)
push (add at end) --> O(1) (can be O(n) if we are dealing with copying and reallocating memory (static arrays))
insert --> O(n)
delete --> O(n)

pop --> remove last item O(1)
unshift --> add item to the beginning of the array, and reassign index O(n)
splice --> add item in middle of array --> shift indexes --> O(n)


Static vs Dynamic arrays

Static --> fixed number of items
Dynamic --> can copy and reallocate the array in a different location with more memory --> if we wanted more memory
Most high level languages will be dynamic arrays --> memory allocation is done automatically O(n)
Low level languages will need to handle the memory allocation


**In interviews --> String questions should be considered as arrays --> split etc then return it as a string after manipulation is done**

Pros and cons of arrays

**Pros**
- fast lookups
- fast push/pop
- ordered

**Cons**
- Slow inserts
- Slow deletes
- fixed size --> if using static array


### Hash Tables
Hash tables = hash maps, maps, unordered maps, dictionaries, objects 

Different names for the same thing --> depends on the langugage

key and value pair

Key --> used as the index as to where to find the object in memory  

hash function --> function that generates a value of fixed length for each input it gets

aspects of hash functions:
- one way only  --> cannot take the hash and get the original input
- will always return the same value for the same input, but as soon as anything changes to the input (e.g Capitalisation) the hash value will change
- **Idempotent** --> always outputs the same 


key --> hash function --> generates hash --> maps it to memory address to store our data

Insert --> O(1)
Lookup --> O(1)
Delete --> O(1)
Search --> O(1)

With Collision --> could be O(n)

Hash Maps -->  Improves time Complexity --> Fast access but more memory

#### Hash Function --> Collisions
Collision --> when the hashfunction allocates the same memory space for 2 items 

![[Pasted image 20220102141453.png]]

![[Pasted image 20220102141702.png]]

There is a possiblity of constantly just adding to the same memory space --> auto assigned
This can slow down our ability to access/insert information
Need to go through each of the items 

Theoretically --> with collisions --> slows down reading and writing of hash tables O(n/k) (k = size of hash table ) --> simplified to O(n)

Collision will most likely happen in any hash table 

Linked list is one way of solving this --> look at wikipedia page for more info 


#### Hash Tabes Vs Arrays
![[Pasted image 20220103113856.png]]

Hash table --> generally faster than arrays
But may have collision issues


arrays are ordered
hash tables --> random

**Pros**
- Fast lookups (good collision resolution needed - usually language helps)
- fast inserts
- flexible keys (you define your own key)

**Cons**
- Unordered
- Slow key iteration (if you want to grab all the keys --> gotta iterate through whole table)


### Linked List
Singley linked list --> Set of nodes (blocks)

Each node has 2 elements --> value of data and a pointer to the next node

First node = Head
Last node = Tail

Linked list are null terminated --> last node points to null

![[Pasted image 20220103175625.png]]

Start at head --> traverse until you reach until the specified Index --> O(n)

array vs linked list
- array --> indexed --> so finds are super fast
- array items are all located next to each other in memory --> faster retrieval 

- linked list --> need to traverse until we find it --> O(n) 
- linked list --> items are scattered all over memory space --> slightly slower retrival compaired to if items are next to each other in memory
- inserting is easier than arrays --> dont need to shift things
- linked list --> has some sort of order --> can have sorted data

![[Pasted image 20220105162211.png]]

Prepend (add at beginning) --> O(1)
append (add at end) --> O(1)
lookup --> O(n) 
insert --> O(n)
delete --> O(n)

Pointer --> reference to another object/node etc

 reference to an object
 
 ``` 
 	val a = 1
    val b = a 
 ```
 
 both a and b  should point to the same location in memory 
 
 
 **Doubly linked list**
 
 has a pointer to the next node as well as a link to the previous node
 
 allows us to traverse backwards
 
 can be slighly more efficient to traverse though the link
 
 downside --> holds more memory 
 
 ![[Pasted image 20220106181406.png]]
 
 **Singly vs Doubly Linked list**
 
 Singly 
 **pros**
 - less memory
 - simpler implementation
 - slighly faster insertion and deletion
  **cons**
 - cannot traverse backwards


doubly 
- can be traversed from both front and back
- can delete the previous node without traversing through whole list --> can go from last node

**cons**
- more complex to implement
- more storage and memory costs

good for search operations


![[Pasted image 20220106194417.png]]

Linked list --> ability to grow and shrink

### Trees

Heirarchal Structure --> can have 0 or more child structure

1 root node
each child / node descends from one parent node

leaf nodes --> very end of the data structure

![[Pasted image 20220108172204.png]]


Linked list --> a type of tree --> linear 

Trees --> nodes can only point to a child

differnet trees for different use cases


#### Binary Tree

Each node can either have 0, 1 or 2 child --> if a node has 3 children --> it is not a binary tree
each node can have 1 parent

![[Pasted image 20220108172734.png]]

![[Pasted image 20220108172922.png]]

perfect binary tree --> all nodes are full --> each node either has 0 or 2 children --> the bottom layer is completely full

Full binary tree --> each node has either 0 or 2 children, never 1 child

Perfect Binary tree --> extremely efficient 
 - number of total nodes in each level doubles as you go down the tree
 - number of nodes in last level = sum of all nodes in the other levles + 1
	 - half the nodes are at the bottom

![[Pasted image 20220108174713.png]]

O(log n) --> really fast (good)

![[Pasted image 20220108175031.png]]

to find # nodes in a tree --> 2^h -1
h = height of tree

log of nodes = height (steps)


#### Binary Search Tree
good at searching and comparing things
this data structure preserves relationships (parent child)

Rules:
1. all child nodes in the tree to the right of the root node must be greater than the current node (going to the left all nodes will decrease, when going to the right all nodes will increase in value)
2. all nodes can only have up to 2 children


https://visualgo.net/en/bst

when deleting nodes --> need to find the node to delete and also the node to replace it in its place


![[Pasted image 20220108175709.png]]


**Balanced vs unbalanced trees**

![[Pasted image 20220108180815.png]]

unbalanced trees --> turns into something similar to linked lists O(n)
balanced trees --> very efficient --> O(log n)


Pros and Cons

![[Pasted image 20220108181026.png]]


**AVL Tree + Red Black trees**

helps with auto balancing trees


#### Binary Heaps
![[Pasted image 20220109184122.png]]

every node on the top level is greater than every node in the level below

commonly used in priority queues

good for doing comparartive operations --> eg find all the nodes < 33

used a lot in data storage, priority queues and sorting algorithms

heaps add values to the tree from left to right then bubbles up/switches items around if its not in the right order

takes up the least amount of space --> never unbalanced 
- preserves order of insertion

![[Pasted image 20220109184749.png]]

#### Priority Queues
each element has a priority --> some have high priority others have low priority

![[Pasted image 20220109185238.png]]


#### Trie 
trie --> sometimes called prefix tree 

specialised tree in searching --> usually text 
- most cases can outperform binary trees, hash tables etc

Tries allow you to know if word or part of a word exists in a body of text

![[Pasted image 20220109185405.png]]

O(length of word)

#### Graph

useful for modeling real life relationships

each item is called a Node(vertix), nodes are connected to other nodes called Edge

can use graphs to represent, friendships, relationships,  networks, cities, 
google maps, facebook etc use graphs

![[Pasted image 20220109192604.png]]

#### Ways to describe Graphs

**Directed vs Undirected Graphs**

Directed --> movement is not bidirectional --> eg. traffic flow

Undirected --> can be bidirectional


**Weighted and Unweighted graphs**

values can be allocated to the edges --> not just nodes

![[Pasted image 20220109192939.png]]


**Cyclic and Acyclic Graphs**

![[Pasted image 20220109193017.png]]


Directed Acyclic Graph (DAG) --> quite common


**Graphs**

![[Pasted image 20220110210735.png]]

good for representing relationships

scaling is difficult 
