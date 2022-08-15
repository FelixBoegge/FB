---
layout: article
title: Pathfinder Visualization
mathjax: true
---

In my second personal project on my way to master Python, I dove into three different path finder algorithms, namely Breath First Search (BFS), Depth First Search (DFS) and A* and the ‘pygame’ library.

The code can be found in the corresponding [repository](https://github.com/FelixBoegge/PathFinder_pygame) on my Github.
To run the application, simply download the [executable file](https://github.com/FelixBoegge/PathFinder_pygame/blob/master/pathfinder.exe), also from my Github and run it in windows. Windows might detect the file as malicious, since it was generated with pyinstaller in PyCharm, but I assure, it contains nothing but the application.

## The Algorithms
BFS, DFS and A* are three different methods to traverse through graphs. BFS basically works with a queue, where all neighboring nodes of the current node are put into the queue. In each iteration the next node will be popped from the queue, set as the current node and in turn it’s neighbors will be added to the queue. Each node that was visited will be added to a ‘visited’ set, to keep track of where we already had been, and to avoid traversing nodes multiple times. In practice, the visited areas spreads circular.

The DFS algorithm works similar but uses a stack to store the neighbors of the current node. Consequently, the algorithm traverses deeply into one direction until it finds the end or a dead end, then it pops off the top of the stack, one by one, until it finds a node, or in other words a new path and traverses into this new direction deeply. It can be seen as a recursive behavior.

The A* algorithm is a bit more complex and already takes the position of the end into account. It uses a heuristic function to determine, the most probably, best direction. In my code, the heuristic function represents the distance of the current node to the end node. In a checkerboard pattern, where legal moves are up, down, left and right, the distance is
Display math:

$$h = |x_{current} – x_{end}| + |y_{current} – y_{end}|$$



In the scope of this project, the weight of an edge between two nodes are not considered, as they are all one. The board is a 50x50 checkerboard with white spots that can be visited and black spots that represent a wall. The checkerboard pattern can be considered a graph, where each node, except the edge nodes, have four neighboring nodes.

## The Visualization
I visualized the board, from here on called the maze and the three algorithms with ‘pygame’, a useful Python library, where a window can be created, and individual elements can be displayed. The figure below shows the initial state of the program, all spots are blank. The first left click on the maze will always create the start spot. Similarly, if the start spot is set the next left click always creates the end spot. Afterwards each left click creates a wall. The mouse can also stay pressed, and when moved, a wall will be drawn along the path of the curser. Similarly, with the right mouse button, every spot can be reset to blank.

On the right-hand side sits the selection bar. Here one of the three algorithms can be selected. After one of the algorithms successfully found a path to the end, the steps, or in other words, how often the current position changed, and the path length are monitored. Furthermore, instead of drawing your own maze, there are four default mazes that can be selected. The ‘Return’ button sets the algorithm back and can also interrupt a running algorithm, but not erase the maze. ‘Reset’ clears the entire maze. ‘Start’ starts the algorithm.

![TeXt Theme](https://raw.githubusercontent.com/felixboegge/FB/master/assets/pathfinder_visualization/initial.jpg)

The following figure shows the running A* algorithm in one of the default mazes. The orange and turquoise spots depict the start and end respectively, red dots indicate spots that have been visited already. Green dots indicate the open spots, they are the current neighbors, that will be set to current in the next iterations. Prior, the A* algorithm already run and the needed steps and the found path length are shown next to the selection button. The third figure shows the maze after the DFS algorithm found a path. As soon as this happens, the path is drawn in purple from the end back to the start. Prior, the A* and BFS algorithms run, the records on the right can be compared.

![TeXt Theme](https://raw.githubusercontent.com/felixboegge/FB/master/assets/pathfinder_visualization/astar_running.jpg)

![TeXt Theme](https://raw.githubusercontent.com/felixboegge/FB/master/assets/pathfinder_visualization/final.jpg)

The BFS and A* algorithm will, by nature, always find the shortest path, but the DFS algorithm might find a way faster. Since the A* algorithm takes the end spot into account, it has an advantage over the BFS.

## Final
To start this project, I was inspired by an [A*/ pygame tutorial](https://www.youtube.com/watch?v=JtiK0DOeI4A&t=4s&ab_channel=TechWithTim), I found on Youtube, created by [‘Tech With Tim’](https://www.youtube.com/c/TechWithTim) a Youtuber from Canada, providing tons of helpful lectures, tutorials and tips around computer engineering and programing, especially in Python. At this point I want to acknowledge his work and thank him for his contribution to my learning process. I adopted his A* algorithm and the basic construct of the pygame visualization. I added the BFS and DFS algorithms. Additionally, do I record the time, expressed in steps and the path length to compare the different algorithms. Further, I implemented a button-class and used it to create buttons for path finder algorithm selection, selection of four different default mazes and return/ reset and start function. The buttons will light up when the user hovers over them with the mouse and the selected algorithm will be depicted in orange.

I had great fun, developing this project. I got an in depth understanding of the different algorithms, grounding the foundation of graph traversal. I had the chance to use simple data structure like stacks and queues, I learned earlier, and created the traversal algorithms with them.

The pygame library is a great way to visualize and has a high satisfaction factor, when you see everything running on your screen. In future, I will work on more projects using pygame.

