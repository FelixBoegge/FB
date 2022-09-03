---
title: Swarm Simulation
tags: TeXt
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---

Welcome to my next project! This time I caught up with an old project, I worked on, in my time as a student in Biomimetics. It was about simulating natural behavior, commonly observable in nature. I was always fascinated by swarm behavior and its decentralized organization. That is why I simulated the collaborative power of an ant colony, where individuals help each other carry food to the nest.
Back then, I used Matlab and plotted the movement of the ants and the objects to carry in a graph, updating every timestep. The code was not running perfectly and contained some bugs.
This new version is coded in Python using the pygame library, like in my [last project]( https://felixboegge.github.io/FB/2022/08/15/PathFinder_Algorithm.html), to visualize the turmoil. I added some features like interactivity with the user and statistical records.
This project was also my first one I created myself from scratch, the preliminary ones are based on tutorials.

## Swarms
Swarms, especially ant colonies are known for their highly collaborative, decentralized behavior. In other words, there is no central unit controlling the individuals of the swarm, instead every element of the swarm acts and reacts in a simple, preprogrammed manner to external stimuli. For example, will ants collaborate and carry heavy objects together. Furthermore, do ants follow each other. They leave a trail of pheromones showing other ants the way. Other ants in turn will find these trails and follow them.
This behavior can easily be seen as an algorithm. I tried to simulate the before mentioned examples in this project and will explain them in more detail in the following.
The goals or wellbeing of a single individual in a swarm is of minor importance, and the swarm itself is the highest good. For more information, I suggest the this [Wikipedia article about swarms](https://en.wikipedia.org/wiki/Swarm_behaviour#Ant_colony_optimization).

## The Simulation
In this simulation, I wanted to demonstrate two swarm characteristics. First, I wanted the ants to collaborate in carrying heavy objects, in this case cookies, to the nest. The idea is that every cookie has an attraction or a visibility to the ants that grows with more ants already waiting at the cookie. Ants initially are strolling around, but as soon as they come inside the visibility of a cookie, they approach it. As soon as there are enough ants for the cookie, they start to carry it to the nest. After fulfilling their mission, they spread out randomly again.
The second imitation illustrates ants following each other. Every ant leaves a trail of pheromones that decays with time. As soon as an ant encounters a trail it has a chance, based on the freshness of the trail, to follow that trail. This swarm feature has the advantage that as soon as the leading ant is finding a cookie, all the trailing ants will approach that cookie. However, there is also a disadvantage. Occasionally it might happen, that the leading ant is finding the pheromone trail of one of its trailing ants, hence forming a deadly cycle. This truly happens in real life too. The ants will chase each other until they die of exhaustion. This phenomenon can be seen in this [YouTube video](https://www.youtube.com/watch?v=LEKwQxO4EZU&ab_channel=AmazeLab). To eliminate death spirals, I implemented an algorithm, detecting such traps and delete participating individuals.

## Rendering
To visualize the swarm behavior, I used the pygame library once more. The simulation starts directly after the file is executed. Some initial ants will randomly start strolling around starting in the middle at the nest. More will spawn over time. Equally, some cookies with random size will be placed randomly and spawn over time. Occasionally, ants have a random chance to alter their orientation by up to 45 degrees. When they hit the boundaries, they bounce off.
Yellow circles indicate the attraction, or visibility of the cookies. Whenever an ant enters such a circle, it will approach the corresponding cookie and wait there. With every ant waiting at the cookie, the yellow circle grows. As soon as a cookie is occupied by enough ants to be carried, they head towards the nest. Upon arrival, the participating ants reach out to find their next mission.
Every ant drags a trail of pheromones, rendered by purple dots that fade into white, depicting the freshness of the pheromone.

## User Experience
To make the simulation more fun to watch, I added some interactivity and records. I implemented some sliders, with which the user can change parameters of the game in real time. They are found on the right-hand side and encompass maximum number of ants and cookies, frequency of new spawned ants and cookies and the velocity of the ants. Additionally, some records are monitored including current number of ants and cookies, available food, collected cookies and accumulated food, ants killed in death cycles and the passed time in seconds.

## Final
 I had great fun working on this project. Swarm behavior and its characteristics excite me for a long time already. I believe it is and will be a great role model for decentralized systems in different fields. For instance, could a swarm of drones of different ´expertise´ collaborate to construct buildings. Or characteristics could be adapted in autonomous driving and transportation. I believe there are and will emerge many other fields of applicability.
I implemented some classes for this project, among others for the sliders, which gave me a more in-depth understanding of pygame. Furthermore, did I implement my own data structure to record the pheromone trails of my ants. A kind of a circular queue, which overwrites itself.

Thank you for reading and following me. To have a look into my code, visit the corresponding [repository]( https://github.com/FelixBoegge/swarm_simulation) on my Github. To run the simulation, simply download the [executable]( https://github.com/FelixBoegge/swarm_simulation/blob/master/Swarm%20Simulation%20executable.rar), unpack it and run the .exe file. Once again, windows might detect the files as malicious, but it only contains the simulation.
If you have any questions or suggestions, feel free to contact me. Have a great day.
