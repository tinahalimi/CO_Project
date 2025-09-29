# Enhancing Decision Trees with Genetic Algorithms

This repository contains the implementation for a Convex Optimization II project exploring how genetic algorithms can improve the performance of single, interpretable decision trees. The work targets the common trade-off between accuracy and interpretability: while ensembles (e.g., Random Forests, Gradient Boosting) often achieve higher accuracy, a single decision tree remains preferable in regulated or high-stakes settings where transparent decision rules are required. By combining bootstrapping, mutation, and crossover operations within a genetic search, this project evolves decision trees toward higher accuracy without abandoning their inherent interpretability.

## Project Overview

Traditional decision tree training relies on greedy, node-by-node optimization, which can lead to suboptimal global structures. This project reframes tree induction as a global search problem. We first generate an initial population of shallow trees via bootstrap samples, then iteratively apply genetic operators to refine structure and thresholds. Candidate trees are evaluated using a fitness function (classification performance on validation folds), and survivor selection with simple elitism retains strong candidates across generations. The resulting approach maintains a single, human-readable tree while narrowing the performance gap with black-box or ensemble models.

## Method

The codebase implements two core components:

- **InternalDecisionTree**: a lightweight, array-based representation of a decision tree (features, thresholds, child pointers, and leaf predictions). This enables efficient copying, mutation of thresholds, subtree composition, and prediction.  
- **GeneticDecisionTree**: a wrapper that (1) builds an initial population of trees on bootstrap samples, (2) applies mutation (threshold perturbations) and crossover (subtree recombination around compatible roots), (3) scores candidates, and (4) selects the best tree over several iterations. Hyperparameters include maximum depth, number of evolutionary steps, and random seeds for reproducibility.

A small test harness demonstrates the approach on a standard tabular dataset, comparing a depth-constrained baseline decision tree against the genetically optimized counterpart.

## Repository Structure

- `src/`  
  - `internal_decision_tree.py`: Array-based tree structure, copying utilities, counting/leaf labeling, and prediction routines.  
  - `genetic_decision_tree.py`: Genetic search loop (population init, fitness evaluation, mutation, crossover, selection).  
- `notebooks/`  
  - `demo.ipynb`: End-to-end demonstration on a benchmark dataset with visualizations.  
- `Report.pdf`: Full project report with background, theory, implementation details, and experiments.  
- `.gitignore`: Ignore rules for local artifacts.

> Note: Filenames may differ from the above; align with your repository’s organization if needed.

## Usage at a Glance

1. Install Python dependencies (e.g., `scikit-learn`, `numpy`, `pandas`, `matplotlib`).  
2. Run the demo notebook in `notebooks/` to train a baseline decision tree and a genetic decision tree and compare performance.  
3. Inspect the final tree structure and thresholds to verify interpretability.

## Key Ideas and Design Choices

- **Global Search vs. Greedy Splits**: Genetic operators explore multiple tree configurations beyond local, greedy choices.  
- **Bootstrapped Starts**: Initial diversity is created by training shallow trees on bootstrap resamples.  
- **Mutation (Threshold Tweaks)**: Small changes to node thresholds can yield meaningful downstream structure changes with minimal complexity cost.  
- **Crossover (Subtree Recombination)**: When compatible, subtrees from strong parents are combined to transfer complementary strengths.  
- **Shallow, Interpretable Trees**: Depth is constrained (e.g., depth 2–5) to preserve readability.


