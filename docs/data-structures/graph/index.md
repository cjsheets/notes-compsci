# Graph

A graph is a data structure where a finite set of objects are connected by links. The object connection points
are called **verticies** and the links are called **edges**. Formally, a graph is a pair of sets **(V, E)**  (verticies and
edges). Example:

> V = {a, b, c, d}
>
> E = {ab, bc, cd, ca}

### Important Terms

* Vertex - represented by an array
* Edge - represented by a 2 dimensional array of 1s and 0s
* Adjacency - Nodes/Verticies are adjacent if they are connected by an Edge
* Path - A sequence of edges that connect verticies

## Depth First Search

Traverse graph by searching "deep" first, using a stack to track progress.

1. Visit an adjacent (unvisited) vertex, mark as visited, push it in a stack.
2. Once no adjacent verticies found, pop the stack until new verticy is found
3. Repeat until stack is empty

## Breadth First Search

Traverse graph by searching "wide" first, using a queue to track progress.

1. Visit adjacent (unvisited) vertex, mark visited, insert in queue.
2. Once no unvisited adjacent vertex available, remove the first queue element and check for verticies.
3. Repeat until queue is empty.