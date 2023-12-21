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
The minimum cost flow problem can be solved by linear programming, since it optimizes a linear function and all constraints are linear. However, your job is to implement two metaheuristic algorithms that solve this problem.

The first algorithm is a simple hill-climbing local search algorithm. Considering that this algorithm falls for local-minimum, you must implement a mechanism to randomly restart it, when the algorithm gets stuck. For this, you must implement the search loop from scratch.

The second algorithm is a single-object genetic algorithm. For this, you can rely on the `pymoo` library.

For both algorithms, the maximum execution budget is `100` iterations/epochs.

Of course, you need to implement the Graph class and the methods to validate whether a given problem (flow network) and solution (allocation of flow) are valid.

Please refer to the existing method signatures to create and validate Graphs as well as solutions.

> Note: You need to implement those methods, but you cannot change their signature!

## Tests

Even if you rely on existing libraries you must test your implementations (Graph, Local Search, etc.)

The target coverage level is 90%