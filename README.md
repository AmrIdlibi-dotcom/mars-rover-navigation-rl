# Q-Learning Agent for GridWorld Navigation

This repository provides a comprehensive implementation and evaluation of a Q-learning agent designed to navigate a procedurally generated `GridWorld` environment. It showcases core reinforcement learning concepts, establishes an A* pathfinding baseline, performs robustness testing, conducts hyperparameter tuning, and offers detailed performance analysis with rich visualizations.

## Table of Contents
1.  [Project Overview](#project-overview)
2.  [Features](#features)
3.  [How to Use](#how-to-use)
4.  [Environment Customization](#environment-customization)
5.  [Key Results and Analysis](#key-results-and-analysis)
6.  [Future Improvements](#future-improvements)
7.  [Dependencies](#dependencies)

## Project Overview

The primary goal of this project is to develop, evaluate, and thoroughly understand the capabilities and limitations of a Q-learning agent in a dynamic `GridWorld` environment. This involved a systematic investigation into how the agent learns to navigate, its performance under varying environmental complexities, and the impact of its internal configurations (hyperparameters).

## Features

*   **Procedural GridWorld Generation**: Customizable `GridWorld` environment with variable size, obstacle probability, and reproducibility via seeding.
*   **Q-Learning Agent Implementation**: A robust Q-learning agent with configurable learning rate (`alpha`), discount factor (`gamma`), and epsilon-greedy exploration strategy.
*   **A* Pathfinding Baseline**: An A* algorithm implementation to provide an optimal pathfinding benchmark for comparison.
*   **Training and Visualization**: Functions for training the Q-learning agent, tracking performance metrics (rewards, steps, success rates), and visualizing the learning progression through animated paths.
*   **Robustness Testing**: Systematic evaluation of the Q-agent's performance across a diverse set of `GridWorld` configurations to understand its resilience to environmental changes.
*   **Hyperparameter Tuning**: Grid search for optimal Q-learning hyperparameters to maximize performance on a representative environment.
*   **Detailed Performance Comparison**: Quantitative and qualitative analysis comparing the optimized Q-agent's performance against the A* baseline on challenging maps.
*   **Comprehensive Reporting**: An integrated final report summarizing findings, insights, strengths, weaknesses, and potential future work.

## How to Use

1.  **Clone the Repository**:
    ```bash
    git clone https://github.com/your-username/Q-Learning-GridWorld.git
    cd Q-Learning-GridWorld
    ```
2.  **Open in Google Colab**: Upload the `q_learning_gridworld.ipynb` notebook to Google Colab.
3.  **Install Dependencies**: The notebook includes all necessary imports. Ensure you have `numpy`, `matplotlib`, `heapq`, `random`, `collections`, `copy`, and `pandas` installed (these are typically pre-installed in Colab).
4.  **Run All Cells**: Execute all cells in the notebook sequentially. The notebook is structured to guide you through environment setup, A* baseline, Q-learning training, robustness testing, hyperparameter tuning, and final performance comparison.

## Environment Customization

You can easily customize the `GridWorld` environment parameters to explore different scenarios:

Locate the `GridWorld` initialization cell (typically in Section 3) and modify the `size`, `obstacle_prob`, and `seed` parameters:

```python
env = GridWorld(size=30, obstacle_prob=0.20, seed=30) # Customize these values
```

*   **`size`**: Dimensions of the square grid (e.g., `30` for a 30x30 grid).
*   **`obstacle_prob`**: Probability (0-1) that a cell will be an obstacle. Higher values create more cluttered environments.
*   **`seed`**: Integer for reproducibility. Changing this generates a new map layout.

**Important**: After modifying these parameters, re-run all subsequent cells to apply the changes to the entire analysis.

## Key Results and Analysis

### Robustness Testing
*   **Impact of Obstacle Probability**: Performance generally degraded with higher obstacle probability. Environments with `obstacle_prob` between 0.10 and 0.20 showed better results.
*   **Impact of Grid Size**: Smaller grids (10x10, 15x15) often led to higher success rates and optimal paths. Performance decreased with increasing `size`, especially combined with high obstacle density.
*   **Path Efficiency**: For many solvable configurations, the Q-agent's paths were either identical or very close to the A* optimal path.
*   **Challenging Configurations**: The agent struggled with very large or highly obstructed environments, and could not solve maps that A* also failed on.

### Hyperparameter Tuning
A grid search was performed on a representative `GridWorld` (`size=20`, `obstacle_prob=0.15`, `seed=201`) to find optimal hyperparameters.

**Optimal Hyperparameters Identified**:
*   `alpha` (Learning Rate): `0.2`
*   `gamma` (Discount Factor): `0.99`
*   `eps_decay` (Exploration Decay Rate): `0.995`

This combination yielded the highest average reward and success rate during tuning, significantly improving learning efficiency.

### Final Performance Comparison

Using the optimized hyperparameters, the Q-learning agent was compared against the A* baseline on selected maps:

*   **Path Efficiency**: In all solvable environments, the optimized Q-agent consistently found paths of the *exact same length* as the A* optimal path, demonstrating excellent path discovery.
*   **Success Rate**: High success rates (74-77%) were observed on easy to medium-complexity maps. For more challenging maps, success rates were moderate (53-61%), with appropriate failure (0%) on intrinsically unsolvable maps.
*   **Average Reward**: While individual successful runs yielded high rewards, the average reward over training episodes could still be negative in complex environments, indicating ongoing exploration failures.

## Future Improvements

To further advance this project, consider exploring:

*   **Advanced Exploration Strategies**: Implement Boltzmann Exploration, UCB, or Curiosity-Driven Exploration to improve learning efficiency.
*   **Deep Q-Learning (DQN)**: Replace the Q-table with a neural network to handle larger state spaces.
*   **Prioritized Experience Replay (PER)**: Integrate PER to improve sample efficiency during training.
*   **SARSA Learning Comparison**: Implement and compare SARSA (on-policy) with Q-learning (off-policy).
*   **Multi-Objective Reinforcement Learning**: Introduce and optimize for multiple reward components.
*   **Dynamic Environments**: Extend `GridWorld` with moving obstacles or changing goals to test adaptability.

## Dependencies

This project requires the following Python libraries:

*   `numpy`
*   `matplotlib`
*   `heapq`
*   `random`
*   `collections` (deque)
*   `copy`
*   `pandas`
*   `IPython.display` (for animations)
*   `matplotlib.animation` (for saving animations)

These can typically be installed via pip:
`pip install numpy matplotlib pandas`
