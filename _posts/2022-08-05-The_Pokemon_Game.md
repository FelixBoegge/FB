---
layout: article
title: The Pokémon Game
mathjax: true
---

Here we go, this is my first personal project on my way to develop strong skills in Python. As a kid, I was a huge Pokémon fan, I especially enjoyed the video games and the trading card game with fascination. That’s why I chose this theme as the one for my small terminal-based game. Furthermore, did I seek to improve my object-oriented programming (OOP) – skills. During my mechatronic studies, years ago, I had my first experience with OOP in C++ and found it as an incredibly useful feature of programming. Based on a YouTube Tutorial ['Python Object Oriented Example Project'](https://www.youtube.com/watch?v=2AK7j8pIh-0&t=21s&ab_channel=CodingNomads) on Channel 'CodingNomads' by 'Martin Breuss', I started refreshing my OOP skills, but this time in Python. I followed Mr. Breuss’ introduction and added more functionality to the Game.

The code for the game can be found in the corresponding [repository](https://github.com/FelixBoegge/the_pokemon_game) on my GitHub.


## The Game
As the game starts, a set of Pokémon with various attributes is instantiated from a csv-file. The game-initialization is depicted in the figure below. In the beginning, the Player chooses a name and how many Pokémon will fight for him in this round, as well as whether he wants to pick his/her Pokémon, or if they get randomly assigned. The opponent gets the same number of randomly assigned Pokémon. Furthermore, the Pokémon-Type-Relationships, described further below, are displayed.

<img class="image image--xs" src="https://raw.githubusercontent.com/felixboegge/FB/master/assets/the_pokemon_game/start.jpg"/>


The Player has different types of actions he/she can execute: (fight, train, heal, show Pokémon-type relationships, show Pokémon, quit). After every action all Pokémon for both players will be displayed with their attributes: number of Pokémon (for selection), name, type, max. & current HP, damage, status; as displayed in the following figure.

<img class="image image--xl" src="https://raw.githubusercontent.com/felixboegge/FB/master/assets/the_pokemon_game/mainscreen.jpg"/>

## Pokémon-Types
There are five different Pokémon-types: fire, water, grass, electric and rock. Each type as advantage over two types and disadvantage over two other types.

## Fight
<img class="image image--xl" src="https://raw.githubusercontent.com/felixboegge/FB/master/assets/the_pokemon_game/fight.jpg"/>

If ‘fight’ is selected, the player can choose one of his/her active Pokémon. If only one active Pokémon remains, it is selected automatically. The Pokémon will fight against an active, randomly selected Pokémon of the opponent. If a Pokémon has a type-advantage over the other, it deals double damage. The Pokémon with disadvantage deals normal damage. If the HP of a Pokémon drops to or below zero, the status of that Pokémon changes to KO and it can't be selected for any further action.

## Train
<img class="image image--xl" src="https://raw.githubusercontent.com/felixboegge/FB/master/assets/the_pokemon_game/train.jpg"/>

If ‘train’ is selected, the Player selects an active Pokémon. Again, if only one active Pokémon remains, it is selected automatically. The trained Pokémon from now on deals a predefined amount more damage in every fight. An active, randomly selected Pokémon from the opponent becomes equally trained. The player can train a predefined number of times.

## Heal
<img class="image image--xl" src="https://raw.githubusercontent.com/felixboegge/FB/master/assets/the_pokemon_game/heal.jpg"/>

If ‘heal’ is selected, the Player selects an active Pokémon, which has not full HP. If no such Pokémon is in the player's list, the game returns to the action selection. Again, if only one active Pokémon with less than full HP remains, it is selected automatically. The healed Pokémon receives a health potion and fills up a predefined amount of HP. An active, randomly selected Pokémon with less than full HP from the opponent becomes equally healed. If no such Pokémon exists, the opponent heals no Pokémon. The player can heal a predefined number of times.

## Show Pokémon-Type-Relationships:
Shows a table of the relationships between the different types. Each type has advantage over two types, disadvantage over two other types and a neutral relationship to itself.

## Show
Shows the status with all attributes of all Pokémon from both players.

## Quit
Immediately ends the game.

The game is over, as soon as each Pokémon of one or both players are KO, or the player leaves the game through the quit action.

## Conclusion
I created this game in a graphically appealing manner, as much as the PyCharm console can spare. I had a lot of fun, working on this project. It is highly visual and interactive, already during the process of coding, you clearly can see your game growing, as more and more features are implemented. I learned a lot about classes, how object design works, how class-inherent methods are implemented and how objects are represented as strings. In addition, I got strongly familiar with strings. 

I hope you enjoy playing the game, as much as I enjoyed programming it.

To play the game, simply download the files: 'main.py', 'pokemon.py' and 'Pokemonlist.csv' from [the-pokemon-game](https://github.com/FelixBoegge/the_pokemon_game) repository in my GutHub, insert them into a new project in PyCharm and run main.py.

If you have any questions or suggestions, feel free to send me an email to felixboegge@googlemail.com.

Acknowledgment to Martin Breuss, who created the tutorial on which this game is based on. It was my first practical experience with classes in Python and my first overall Python project. 

Stay tuned for more interesting projects in the future!
