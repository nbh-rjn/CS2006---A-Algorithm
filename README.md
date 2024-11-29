# CS2006 Operating Systems Project

## Problem Description
A variation of **Dijkstra's Algorithm**, A* is an informed search algorithm or best-first search. It operates on weighted graphs and aims to find the path from a starting node to a goal node with the smallest cost (e.g., shortest distance or time). The algorithm maintains a tree of paths originating at the start node and extends these paths one edge at a time until it meets its termination criteria.

---

## Objective
**Apply multithreading to the A* Search Algorithm.**  
By distributing the array across threads, we improve efficiency by finding the shortest path and lowest cost through parallel execution.

---

## Details
Although a variation of Dijkstra's Algorithm (which finds the shortest path by selecting edges with the least cost), A* is faster as it uses **heuristic values** to estimate path quality.  
In this project, we used the **Manhattan Distance** strategy (based on Pythagoras’ Theorem) to compute the heuristic value on a rectangular grid.

### Formula:
- **f = g + h**  
  - `g` = Dijkstra distance  
  - `h` = heuristic distance  
  - `f` = resultant sum  

**Visual Representation:**  
The vertices and edges modeled on a square grid, as seen by the algorithm:

![Grid Representation](https://github.com/user-attachments/assets/53f033af-6d18-4c5b-b215-24804ab7c4cf)  
![Algorithm Path](https://github.com/user-attachments/assets/b9971c57-7f24-491b-87a3-bd4f43f91087)

---

## Multithreading Application
In the main algorithm, paths are explored sequentially in all directions. By leveraging multithreading:  
1. Each of the **eight directions** is assigned to a separate thread.  
2. Paths in all directions are explored simultaneously.  
3. Parallel execution ensures improved performance without affecting correctness.

### Implementation:
```cpp
pthread_t T[8]; 
pthread_create(&T[0], NULL, firstSuccessor, NULL);
pthread_create(&T[1], NULL, secondSuccessor, NULL);
pthread_create(&T[2], NULL, thirdSuccessor, NULL);
pthread_create(&T[3], NULL, fourthSuccessor, NULL);
pthread_create(&T[4], NULL, fifthSuccessor, NULL);
pthread_create(&T[5], NULL, sixthSuccessor, NULL);
pthread_create(&T[6], NULL, seventhSuccessor, NULL);
pthread_create(&T[7], NULL, eighthSuccessor, NULL);

for (int i = 0; i < 8; i++) pthread_join(T[i], NULL);


Results
Applying multithreading concepts to the A-Star Search algorithm yields quicker results and more efficient utilization of resources, as multiple directions are explored simultaneously. 
In addition to multithreading, the code has been amended for clarity and clear output of the grid, intended source and destination cells, and path followed.

Output
Windows:
![image](https://github.com/user-attachments/assets/5695e992-1476-4436-a970-5ceca3e84249)
![image](https://github.com/user-attachments/assets/0c2f05f7-f5a7-487a-aee8-150c45de7461)

Linux(Ubuntu):
![image](https://github.com/user-attachments/assets/c2f2b37a-644d-4c7b-a1f4-ef2eec8c1bbf)
![image](https://github.com/user-attachments/assets/509cfabf-1acd-4502-98a3-cf61244f340c)

 
Conclusion
The shortest path from each source vertex to the destination vertex has been successfully obtained by utilizing heuristic values across threads.

Tools, Technology and Resources
Learning and references:
https://youtu.be/eSOJ3ARN5FM 
https://www.geeksforgeeks.org/a-search-algorithm/ (non-multithreading)

Language: C++
Tools: Visual Studio 2019, Dev C++, Oracle VM VirtualBox (Ubuntu 22.04)




