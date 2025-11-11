# Spectral Modularity Community Detection on Karate Club Graph

## Project Overview

This project implements a spectral modularity-based community detection algorithm using recursive bisection on Zachary's Karate Club network. The implementation is part of the DSC212: Graph Theory Module research assignment.

## Assignment Requirements

### What Was Required

1. **Implement Recursive Spectral Modularity Partitioning**
   - Build modularity matrix: $B = A - \frac{kk^T}{2m}$
   - Use eigenvalue decomposition for spectral bisection
   - Apply recursive bisection until no beneficial splits remain (eigenvalue stopping criterion: $\lambda_1 \leq 0$)

2. **Visualize Community Evolution**
   - Display the graph after each split with communities colored differently
   - Use consistent node labeling across visualizations
   - Show modularity gain ($\Delta Q$) for each split

3. **Compute Network Centrality Metrics**
   - Degree centrality
   - Betweenness centrality
   - Closeness centrality
   - Clustering coefficient
   - All metrics computed on the **full graph** after each split

4. **Track Metric Evolution**
   - Plot how each node's metrics change across iterations
   - Provide statistical analysis of metric trends

5. **Written Analysis**
   - Identify nodes that remain consistently central
   - Explain how community structure influences centrality metrics
   - Compare results with known ground truth (historical club split)

## What Was Implemented

### Core Algorithm
-  **Modularity Matrix Construction**: Implemented subgraph-based modularity calculation
-  **Spectral Bisection**: Leading eigenvector computation using `scipy.linalg.eigh`
-  **Recursive Detection**: Pre-order traversal with eigenvalue stopping criterion
-  **Partition Tracking**: Linear reconstruction of community evolution from recursive tree

### Visualization Components
-  **Split Grid Visualization**: Shows graph state after each split in a grid layout
-  **Fixed Spring Layout**: Consistent node positioning across all iterations
-  **Color-Coded Communities**: Unique colors for each community with modularity gain labels

### Metric Computation
-  **Global Metrics**: All four centrality measures computed on full graph (not per community)
-  **Time Series Tracking**: Stores metric values for all nodes across all iterations
-  **NetworkX Integration**: Uses built-in functions for standardized metric calculation

### Analysis & Reporting
-  **Metric Evolution Plots**: 
  - Combined 2×2 grid showing all four metrics
  - Individual detailed plots with legends
-  **Written Discussion**: Analysis of central nodes and community influence on metrics

## Technical Stack

- **Python 3.x**
- **NetworkX**: Graph data structure and centrality computations
- **NumPy**: Matrix operations and numerical computing
- **SciPy**: Eigenvalue decomposition
- **Matplotlib**: Visualization and plotting


## Mathematical Foundation

**Key formulas:**
- Modularity Matrix: $B = A - \frac{kk^T}{2m}$
- Modularity Gain: $\Delta Q = \frac{s^T B s}{4m}$
- Stopping Criterion: Split only if $\lambda_1 > 0$

## Results

The algorithm successfully:
- Detected multiple communities in the Karate Club network
- Tracked centrality evolution across 5+ split iterations
- Identified consistently central nodes (hubs and bridges)
- Validated against known historical split (Mr. Hi vs. Administrator factions)

