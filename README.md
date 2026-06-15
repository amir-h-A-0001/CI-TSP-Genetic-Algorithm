# Traveling Salesman Problem using Genetic Algorithm

A from-scratch implementation of a Genetic Algorithm (GA) for solving the Traveling Salesman Problem (TSP).

This project was developed as part of a Computational Intelligence course and demonstrates how evolutionary algorithms can be applied to combinatorial optimization problems.

## Overview

The Traveling Salesman Problem (TSP) aims to find the shortest possible route that visits every city exactly once and returns to the starting city.

This implementation uses a Genetic Algorithm to evolve increasingly shorter routes over multiple generations.

## Features

- Random population initialization
- Tournament selection
- Ordered Crossover (OX)
- Inversion Mutation
- Fitness-based evolution
- Route visualization
- Convergence plotting
- Reproducible experiments using random seeds

## Representation

Each chromosome is a permutation of city indices:

```text
[4, 1, 0, 3, 2, 5]
```

representing the order in which cities are visited.

## Fitness Function

The objective is to minimize the total route length.

Since Genetic Algorithms traditionally maximize fitness, fitness is defined as:

```text
fitness = 1 / total_distance
```

Higher fitness therefore corresponds to shorter routes.

## Genetic Operators

### Selection

Tournament Selection is used to choose parents for reproduction.

### Crossover

Ordered Crossover (OX):

1. A random segment is copied from Parent A.
2. Remaining cities are filled using the order of Parent B.
3. Valid permutations are preserved.

### Mutation

Inversion Mutation:

1. A random segment of the route is selected.
2. The order of cities within that segment is reversed.

## Workflow

For each generation:

1. Evaluate population fitness.
2. Record the best chromosome.
3. Select parents using tournament selection.
4. Generate offspring via crossover.
5. Apply mutation with a configurable probability.
6. Replace the population with the new generation.

## Dataset

The notebook can generate random 2D points automatically:

```python
NUMBER_OF_POINTS = 50
X_RANGE = (0, 100)
Y_RANGE = (0, 100)
```

Points are saved as CSV files and used to construct the distance matrix.

## Distance Matrix

Pairwise Euclidean distances are computed using NumPy:

```python
dist_matrix[i][j]
```

stores the distance between city *i* and city *j*.

## Example Hyperparameters

```python
POP_SIZE = 500
REPS = 700
K = 4
MUT_RATE = 0.05
SEED = 43
```

where:

- `POP_SIZE` = population size
- `REPS` = number of generations
- `K` = tournament size
- `MUT_RATE` = mutation probability

## Results

The notebook produces:

### Convergence Plot

Tracks the best route length found in each generation.

### Route Visualization

Displays the final tour connecting all cities.

### Final Solution Quality

Reports the total path length of the best chromosome found.

## Requirements

```bash
pip install numpy matplotlib
```

## Running

Open the notebook:

```bash
jupyter notebook TSP.ipynb
```

and execute all cells.

## Project Structure

```text
.
├── TSP.ipynb
├── test_points.csv
└── README.md
```

## Educational Purpose

This project demonstrates the core components of a Genetic Algorithm:

- Population initialization
- Fitness evaluation
- Selection
- Crossover
- Mutation
- Evolutionary optimization

without relying on external optimization libraries.