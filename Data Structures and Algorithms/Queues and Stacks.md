#interview 
### Stacks and Queues 

linear data structures where we can go traverse through them one by one

Main difference between the 2 is how items get removed

commands --> push, pop, peek, lookup
only for the first and last element 

#### Stacks
LIFO --> Last in First Out

think of it like a stack of plates --> can only access the top one (cant access the bottom one until the end)

methods:
POP --> remove last item
Push --> add an item
Peek --> view the last item

Can be implemented using Arrays or Linked list
Both can be used
Arrays --> has cache locality (slightly faster) 
Linked list --> has extra memory --> but more dynamic memory

### Queues
FIFO --> First in First Out

Think of it like Queuing for something --> first person who arrives gets to go first 

methods
enqueue (push) -->  add to queue
dequeue (pop) --> remove from queue --> removes the first element
peek --> view the first element

Should use linked lists --> otherwise if using arrays when we remove the first item we will need to shift indexes for all of the items in the queue


