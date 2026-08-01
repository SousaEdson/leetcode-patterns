# Java Data Structures CheatSheet - Heap    
A heap is a data structure used to store elements with the following property: The head of the queue is always the smallest element (for a min-heap) or the biggest element (for a max heap). In java, priority queue is implemented through the PriorityQueue class.   
Heaps are implemented using an array, but can be visualized as a complete binary tree, where each subtree has the heap property: Both nodes must be less than the parent node. New nodes are added at the last free position from left to right. If the new element is bigger than its parent, it will bubble up until it reaches it final destination.

## Useful methods

`new PriorityQueue<>(int initialCapacity)`   
Initialize a new heap with a default initial capacity. Even though it has a capacity, it can grow as needed.   

`new PriorityQueue<>(Comparator comparator)`     
Initialize a new heap with a custom comparator. Useful for creating heaps with any kind of ordering, such as max heaps, for example.
Example of a heap that orders elements based on its parity:
```java
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(
  (a, b) -> {
      if((a % 2 ) == (b % 2)){
          return Integer.compare(a, b);
      }
      return Integer.compare(b%2, a%2);
  }
);
```

Example of a max heap:   
```java
PriorityQueue<Integer> priorityQueue = new PriorityQueue<>(Comparator.reverseOrder());
```

`new PriorityQueue<>(int initialCapacity, Comparator comparator)`   
Combine the last two constructors: Create a heap with initial capacity and a custom comparator.

`priorityQueue.peek()`
returns the top of the heap without removing the element from the heap. $O(1)$ time complexity.

`priorityQueue.poll()`   
returns the top element and remove it from the heap. $O(log(n))$ time complexity.


`priorityQueue.offer()`   
adds a new element to the heap. $O(log(n))$ time complexity.


