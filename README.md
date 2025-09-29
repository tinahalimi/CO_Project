# Enhancing Decision Trees with Genetic Algorithms

This repository contains the implementation and analysis for a project in *Convex Optimization II* at Sharif University of Technology. The project investigates how genetic algorithms can improve the performance of single decision trees, balancing the trade-off between predictive accuracy and interpretability. While ensemble methods such as Random Forests and Gradient Boosting often outperform individual trees, they lack transparency. This work demonstrates how evolutionary strategies can enhance accuracy while preserving the interpretability of a single tree model.

---

## Project Overview

Conventional decision tree algorithms rely on greedy, node-by-node optimization, which frequently leads to locally optimal but globally suboptimal trees. To address this limitation, we reformulate tree induction as a global search problem guided by evolutionary principles.  

The approach begins with an initial population of shallow trees generated via bootstrap sampling. Genetic operators, including **mutation** (threshold perturbation) and **crossover** (subtree recombination), are applied iteratively to evolve candidate trees. Fitness evaluation is based on classification performance, and elitist survivor selection ensures that strong candidates persist across generations. The final output is a single, interpretable decision tree with improved generalization compared to its greedy counterpart.

---

## Repository Contents

- `Implementation.ipynb`: Jupyter Notebook implementing the genetic decision tree framework and experiments.  
- `Report.pdf`: Detailed project report including background, methodology, and results.  
- `Presentation.pdf`: Project presentation slides.  

---

## Key Contributions

- Reformulated decision tree learning as a **global optimization problem** using evolutionary search.  
- Developed a lightweight internal tree representation enabling efficient mutation, crossover, and evaluation.  
- Demonstrated how **bootstrapping, mutation, and subtree crossover** can improve tree accuracy without compromising interpretability.  
- Highlighted the practical value of shallow, transparent trees in scenarios where model transparency is critical.  

---

## Authors

- **Tina Halimi**  
- **Heliya Shakeri**  
