# Travelling-Salesman-Problem-using-Genetic-Algorithm

## Overview
- **Objective:** Find the shortest possible route that visits each city exactly once and returns to the origin city.
- **Applications:** Logistics, planning, manufacturing, and more.

## Problem Definition
- **Given:** A list of cities and the distances between each pair of cities.
- **Goal:** Determine the shortest path that visits all cities once and returns to the starting point.

## Solution Approaches

### Exact Algorithms
- **Brute Force:**
  - Check all possible permutations of city visits.
  - **Pros:** Guarantees the optimal solution.
  - **Cons:** Computationally expensive (O(n!)).

- **Dynamic Programming (Held-Karp Algorithm):**
  - Use dynamic programming to store intermediate results.
  - **Pros:** More efficient than brute force (O(n^2 * 2^n)).
  - **Cons:** Still exponential time complexity.

### Approximation Algorithms
- **Nearest Neighbor:**
  - Start at an arbitrary city, repeatedly visit the nearest unvisited city.
  - **Pros:** Simple and fast.
  - **Cons:** Does not guarantee the optimal solution.

- **Minimum Spanning Tree (MST) Based:**
  - Create an MST, double the edges, and find an Eulerian circuit.
  - **Pros:** Provides a good approximation.
  - **Cons:** May not yield the shortest possible route.

- **Christofides' Algorithm:**
  - Combines MST, minimum weight perfect matching, and Eulerian circuit.
  - **Pros:** Guarantees a solution within 1.5 times the optimal solution.
  - **Cons:** More complex than nearest neighbor.

## Heuristic Methods
- **Simulated Annealing:**
  - Probabilistically decide whether to accept worse solutions to escape local minima.
  - **Pros:** Can find good solutions in reasonable time.
  - **Cons:** May require parameter tuning.

- **Genetic Algorithms:**
  - Evolve a population of solutions using selection, crossover, and mutation.
  - **Pros:** Can handle large, complex search spaces.
  - **Cons:** May not always find the optimal solution.

- **Ant Colony Optimization:**
  - Simulate the behavior of ants to explore paths and find the shortest route.
  - **Pros:** Effective for large TSP instances.
  - **Cons:** Computationally intensive.

## Use Cases
- **Logistics and Supply Chain:**
  - Optimize delivery routes for cost and time savings.
- **Manufacturing:**
  - Minimize the movement of machines and tools in a factory.
- **Planning:**
  - Optimize travel itineraries for tourism or business trips.

## Genetic Algorithms
Inspired by nature’s process of eliminating things that don’t work, and progressing with things that work.

We work with a population of individuals — each individual is basically a solution to the problem. We pick the individuals who seem to be better solutions, and use those to create a new population. And repeat this process.

## Selection Processes
- **Evaluating solutions or individuals in your population**
- **Using a selection strategy to select the ones you want to keep**

### Evaluating
- Creating some function that takes in the individual or solution as input, and outputs a quantitative estimate — or a fitness score — a number indicating how good it is as a solution.
  - **NOTE:** Choose the evaluation function carefully — a wrong choice would lead you to a wrong kind of solution, and you’ll end up thinking the whole algorithm sucks. A wrong evaluation function won’t throw an error, it will just take you to a different kind of solution. Make sure a high scoring solution is always preferable over a low scoring solution.

### Selection Strategies
- **Roulette Wheel Selection**
  - Every solution is assigned a probability.
  - The probability is based on the fitness score — the more fit the solution, the higher the probability.
  - The probabilities of getting picked as a fit solution is proportional to the fitness — double fitness means double probability.
  - **NOTE:** There is a rank selection method which is similar, it assigns probabilities, but not proportional to the fitness. It gives each solution a ranking based on their fitness and then assigns probabilities. So double the fitness does not mean double the chance of getting picked. In some cases, this helps maintain diversity.

- **Tournament Selection**
  - Pick `n` random solutions from the population.
  - Select the best of that subset (those `n` solutions) as a fit solution. Or a fit parent for crossover.
  - Repeat `K` times to get `K` parents.
  - **NOTE:** There are some other methods (less important) like Steady state method and elitist method — where some individuals from the population just live on as it is to the next generation. Why change it if it is good? Right? Just replacing the medium or poor performers with variants of the good solutions.

## Crossover Strategies
For discrete arrays:

- **One point crossover**
- **Two point and k-point crossover**
- **Uniform crossover**
  - Each element in the offspring is picked from parent A or parent B with equal probability.
  - **NOTE:** For simplicity, I’m skipping real value genome crossover and how to crossover for permutations (like in the traveling salesman problem). You can find it with a google search if you’re interested, but it is very problem-specific and hard to remember, so you can skip it. The general idea is to take some part of the permutation from one parent, and the remaining cities or values from the other parent and use its ordering to place the elements.

## Mutation Strategies
- **Bit Flips:** Randomly flipping bits in the genetic representation of a solution.
- **For Permutations:** Implementing swaps or inversions to introduce variability.