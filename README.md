# ASDII#ILV WS23/24 Assignment Description

## Repo Structure
This repository has the following structure:

```
.
├── README.md
├── __init__.py
├── requirements.txt
└── tests
    ├── __init__.py
    └── test_smoke_test.py
```

> **NOTE** the content of this repository may change as the result of in-class discussion or the definition of new public test cases (new files inside the `tests` folder). Make sure you always check out the latest version of this repository from GitHub!

## Task Description

The goal of this assignment is to solve a classical optimization problem called the **Minimum-cost flow problem**.

According to Wikipedia, the minimum-cost flow problem (MCFP) is an optimization and decision problem to find the **cheapest** possible way of sending a certain amount of flow through a flow network (represented as a Directed Acyclic Graph). 

### Definition
A **flow network** is a directed graph G=(V,E) with a **source** vertex s ∈ V and a **sink** vertex t ∈ V \ s (i.e., t must be different than s!)

Each edge e ∈ E has a finite capacity `cap` and a cost-per-unit-of-flow `cost`.

> Note: capacity and cost must be strictly positive (i.e., cap > 0 and cost > 0)

The cost of sending some units of flow `f` along an edge `e` is `f * e.cost`

The problem requires that the total amount of flow `d` to be sent from source `s` to sink `t`; consequently, `t` must be reachable from `s` and the total capacity of the path(s) between  them must be greater than  `d`, the amount of flow to send.

Valid solutions are those that can make all the units of flow traverse the network from `s` to `t` while not exceeding the capacity of the flow network edges'.

### Optimization Problem

The definition of the problem is to **minimize the total cost of the flow over all edges** under the following constraints:

Capacity constraints: the flow passing thought an `e` must be less or equal to the edge's capacity for all the edges in E

Flow conservation:	 except for vertices `s` and `t`, the amount of flow entering in each vertex `v` must be the same exiting the `v`. In other words, vertices do not suck or produce any flow.

Required flow: the amount of flow **existing** from `s` is equals to `d`; conversely, the amount of flow **entering** into `t` is equals to `d`.

## Solution
The minimum cost flow problem is usually solved using linear programming. However, your job is to implement two metaheuristic algorithms that solve this problem.

For both algorithms, the maximum execution budget is `100` iterations/epochs.

### Task 1: Local Search
The first algorithm is a simple hill-climbing local search algorithm. Considering that this algorithm tends to get stuck in local-minima, you must implement a mechanism to restart it (e.g., when the algorithm gets stuck). To solve this task, you must implement the basic hill climbing search loop from scratch.

### Task 2: Evolutionary Search
The second algorithm that you must implement is a single-object genetic algorithm. For this, you can rely on the `pymoo` library. Thus, your job is to cast/define the flow optimization problem (fitness function, encoding of the solutions, etc.)

### Task 3: Basics
Of course, you need to implement the Graph class and all the necessary methods to check the quality/validity of the found solutions.

### Remarks
Please refer to the given method signatures and implement them without adding/removing parameters.

## Tests

Test your solution and achieve the target coverage level, i.e., 90% stmt coverage