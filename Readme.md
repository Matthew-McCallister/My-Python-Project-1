
## Introduction

In this project, I implement four search algorithms --- DFS, BFS, UCS, and A* --- in `search.py` so that a Pacman planning agent can complete the search problem. I chose to implement the "graph" search rather than the "tree" search version.

Download or clone this repository. This code, and the idea for the assignment, comes from [UC Berkeley](https://inst.eecs.berkeley.edu//~cs188/pacman/home.html).

* Open up the Windows Command Line or Mac Terminal or Linux Terminal.

* Change your directory to the folder with the Pacman code. You should see a file called `commands.txt` and four folders: `py`, `layouts`, `test_cases` and `images`. You will also see a PPT file `HW1_introduction.pptx`, which I will go through in the lecture.

* Run some of these commands (as listed in `commands.txt`) to make sure your setup works. Below are some examples:

```
python3 py/pacman.py
```

```
python3 py/pacman.py --layout tinyMaze --pacman GoWestAgent
```

* Make sure you can execute Pacman. See what happens when you run the following command:

```
python3 py/pacman.py --layout tinyMaze --pacman GoWestAgent
```

## Implementation (in `search.py`)
* Please use python3 and write your own solutions from scratch. Do not import any packages yourself except for those we have included and specified.

* Please only implement your code at where we indicate.

* Please implement the "graph" search version, not the tree search version of each algorithm. That is, you will create a closeset, and you will not expand the already expanded states again.

* In defining the close-set, please simply create a "set" (or "list") and insert visited/expanded states into the closed-set by yourself. There is a "self.expanded" variable in `searchagent.py`, but we highly suggest that you do NOT use that variable since our grading script may not check it.

* Once you finish your implementation, you can execute the autograder by

```
python3 py/autograder.py
```
* Please also read **Other information** at the end of this page for some other hints.


## Task 1: Depth-First Search (DFS)

Open the file `py/search.py` and find the function [`depthFirstSearch`](./py/search.py#L70).

Take the provided template and finish the code (at "YOUR CODE HERE") so that depth-first search works. To do so, please first check the class [`SearchProblem`](./py/search.py#L16). This class outlines the structure of a search problem. It provides functions like `getStartState`, `isGoalState` (i.e., goal test), `getSuccessors`, and `getCostOfActions`. In your implementation, you will be using these functions to get necessary information about the search problem. Please note that, this is a abstract class that we put here to help you understand a search problem. The details of the class is implemented in some other .py files by us already.

Put the successors into the fringe in either the right-to-left or left-to-right fashion. (if you do anything else, it will break the autograder.)

You can test it with Pacman by running the following command:

```
python3 py/pacman.py -l mediumMaze -p SearchAgent -a fn=dfs
```

## Task 2: Breadth-First Search (BFS)

Open the file `py/search.py` and and find the function [`breadthFirstSearch`](./py/search.py#L90).

Take the template and finish the BFS algorithm (at "YOUR CODE HERE").

Put the successors into the fringe in either the right-to-left or left-to-right fashion. (if you do anything else, it will break the autograder.)

You can test it with Pacman by running the following command:

```
python3 py/pacman.py -l mediumMaze -p SearchAgent -a fn=bfs
```


## Task 3: Uniform Cost Search (UCS)

Open the file `py/search.py` and find the function  [`uniformCostSearch`](./py/search.py#L96).

You can test it with Pacman by running the following command:

```
python3 py/pacman.py -l mediumMaze -p SearchAgent -a fn=ucs
```

(Note that adapting your implementation of DFS or BFS maybe useful for UCS.)


### Useful Python code

Task 3 above asks you to implement UCS for Pacman. So, you want to have an open set that's ordered by the accumulated cost. You may use `heaps` for this purpose. Whenever you `pop` a value from a heap, the lowest value comes out. Use a tuple to keep the value and other data together. For example:

```
from util import heappush, heappop
openset = []
heappush(openset, (5, "foo"))
heappush(openset, (7, "bar"))
heappush(openset, (3, "baz"))
heappush(openset, (9, "quux"))
best = heappop(openset)
print(best)
```

Alternatively, you can use the `PriorityQueue` data structures provided to you in `py/util.py`!


## Task 4 (12.5 pts): A* Search

Open the file `py/search.py` and find the function  [`aStarSearch`](./py/search.py#L109).

Finish the implementation of A* search (at "YOUR CODE HERE"). You can use the argument heuristic as a function: `dist = heuristic(state, problem)`. That is, try `h_start = heuristic(problem.getStartState(), problem); print(h_start)`. The class [`nullHeuristic`](./py/search.py#L102) outlines the input and output of a heuristic function. We have implemented the heuristic funcstions.

You can test it with pacman by running the following command:

```
python3 py/pacman.py -l mediumMaze -p SearchAgent -a fn=astar,heuristic=manhattanHeuristic

```


####  Files I edited and submitted:
* `py/search.py`: Where the search algorithms reside.

#### Files you'll want to take a look at:
* `py/searchAgents.py`: Where all search-based agents are defined.
* `py/util.py`: Useful data structures you'll need for defining search algorithms.

#### Supporting files you can ignore (unless you're curious):
* `py/pacman.py`: The main file that runs Pacman games. This file describes a `Pacman` `GameState` type, which you use in this project.
* `py/game.py`: The logic behind how the Pacman world works. This file describes several supporting types like `AgentState`, `Agent`, `Direction`, and `Grid`.
* `py/graphicsDisplay.py`: Graphics for Pacman
* `py/graphicsUtils.py`: Support for Pacman graphics
* `py/textDisplay.py`: ASCII graphics for Pacman
* `py/ghostAgents.py`: Agents to control Ghosts
* `py/keyboardAgents.py`: Keyboard interfaces to control Pacman
* `py/layout.py`: Code for reading layout files and storing their contents
* `py/autograder.py`: Project autograder
* `py/testParser.py`: Parses autograder test and solution files
* `py/testClasses.py`: General autograding test classes
* `py/test_cases/`: Directory containing the test cases for each question
* `py/searchTestClasses.py`: Testcases to support autograding
