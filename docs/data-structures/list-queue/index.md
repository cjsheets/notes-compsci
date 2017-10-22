# Lists, Queues and Stacks




## Challenges - Javascript


### Stack and Queue

-----

**Question:** Implement a stack and queue.

**Answer:** The stack and queue data structures already exist in the form of arrays with push, pop and shift operators.

``` javascript
var myStack = [];

myStack.push(1);
myStack.push(2);
myStack.pop();

var myQueue = [];

myQueue.push(1);
myQueue.push(2);
myQueue.shift();

```

### Priority Queue

-----

**Question:** Implement a priority queue.

!!! note "ToDo"
    Implement a priority queue


### Linked List

**Question:** Advantages/Disadvantages? Implement a linked list.

**Answer:** See [Wikipedia](https://en.wikipedia.org/wiki/Linked_list#Singly_linked_list) for benifits.

They use more memory than arrays due to the addition of pointers. They're limited to sequential access.

In choosing, if you need fast appending/prepending use linked-list or fast index based retrieval of data (array).

Implemented in [ads-ts.LinkedList](https://github.com/cjsheets/ads-ts/tree/master/demo/linked-list). Methods work on the fundemental
"Node" data structure.

```typscript
interface INode<T> {
  item: T;
  next?: INode<T>;
}
```

-----

**Question:** Reverse a SLL (singly linked list).

Implemented in [ads-ts.LinkedList](https://github.com/cjsheets/ads-ts/tree/master/demo/linked-list). Requires O(n) time, touching each element once.

-----

**Question:** Find the middle of a SLL.

Move one pointer at single and one at double steps. When the fast pointer reaches null, the slow pointer is in the middle.

-----

**Question:** Detect a loop in a SLL.

**Answer:** 

Floyd’s Cycle-Finding Algorithm requires a slow and fast pointer. Move a pointer at once "next" per itteration and a second at two "nexts"
per itteration. Compare them. If they're equal before the fast pointer === "null" there is a loop.

Alternatively, you could store objects in a hash table and look for repeats that way. You could also append data (like a "visited" flag)
to nodes to indicate you've seen it before. 

-----

**Question:** Remove a loop in a SLL.

From [GeeksforGeeks](http://www.geeksforgeeks.org/detect-and-remove-loop-in-a-linked-list/)

1. Detect Loop using Floyd’s Cycle detection algo and get the pointer to a loop node.
2. Count the number of nodes in loop. Let the count be k.
3. Fix one pointer to the head and another to kth node from head.
4. Move both pointers at the same pace, they will meet at loop starting node.
5. Get pointer to the last node of loop and make next of it as NULL.

-----

**Question:** Determnine the size of a SLL.

Ideally, count when you add and remove so size is always available.

If not, traverse the list if you can assume there are no loops. If you can't assume that, you need to run loop-detection mentioned above,
find the looped node, and use the combination of head -> loop node + loop length.

-----

**Question:** Find the intersection of two SLL in a single itteration.

from [GeeksforGeeks](http://www.geeksforgeeks.org/write-a-function-to-get-the-intersection-point-of-two-linked-lists/)

1. Get length of both lists
2. Calculate the difference of lengths d = abs(c1 – c2)
3. Now traverse the bigger list from the first node till d nodes 
4. Traverse both the lists in parallel till we come across a common node.

Otherwise, use a hash map

-----

**Question:** sort Linked list


**Question:** Remove duplicate from unsorted LL

**Question:** Check whether a linked list is a palindrome



### Doubly Linked List

Similar to a linked list but with pointers back to the previous element

```typscript
interface INode<T> {
  item: T;
  next?: INode<T>;
  previous?: INode<T>;
}
```

!!! note "ToDo"
    Implement a doubly linked list

-----

**Question:** Reverse a DLL.
