# Adaptive Conversational Strategy Alignment Demo

## Project Overview

This project demonstrates a system for dynamically optimizing a chatbot's conversational strategies over time. It uses principles from Optimal Transport (OT) to adapt the probability of selecting different pre-defined conversational "flows" based on their observed historical performance (success rate) and designer-specified intrinsic costs.

The core idea is to allow a chatbot to:
1.  Be designed with multiple ways (flows) to handle a specific user intent.
2.  Assign a "cost" to each flow (representing complexity, resource usage, etc.).
3.  Continuously learn from user interactions which flows are most effective.
4.  Use Optimal Transport to find the most cost-efficient way to shift its strategy towards empirically successful flows, balancing effectiveness with cost.
5.  Adapt "over time" to improve user experience and operational efficiency.

This demo is implemented as a Jupyter Notebook that simulates user interactions and visualizes the learning process.

## Key Concepts Demonstrated

*   **Intent-Based Flow Management:** Defining multiple conversational paths (flows) for each user intent.
*   **Cost Assignment:** Attributing a cost to each flow, representing factors beyond just success (e.g., complexity, time, resources).
*   **Probabilistic Flow Selection:** Choosing flows based on a learned probability distribution.
*   **Learning from Feedback:** Updating observed success rates for each flow based on interaction outcomes.
*   **Optimal Transport (Sinkhorn Algorithm):**
    *   The chatbot's current strategy (distribution over flows) is considered a source distribution (μ).
    *   A target strategy, derived from observed success rates, is the target distribution (ν).
    *   A cost matrix, based on the intrinsic costs of choosing target flows, is defined.
    *   The Sinkhorn algorithm computes an optimal transport plan to shift μ towards ν while minimizing transport cost (considering regularization).
*   **Strategy Adaptation:** The chatbot's internal preferences for flows are updated based on the optimal transport plan, leading to an evolving strategy.
*   **Persistence:** Saving and loading the learned state so the system can improve continuously across sessions.

## Files in the Demo

*   `adaptive_chat_demo.ipynb`: The main Jupyter Notebook containing all the code, explanations, simulation, and visualizations.
*   `optimizer_state_notebook.json` (generated): Stores the learned state of the optimizer (flow preferences, observed counts). Delete this file to start the simulation fresh.
*   `README.md`: This file.

## Prerequisites

To run this demo, you will need Python 3.x and the following libraries:

*   **NumPy:** For numerical operations.
*   **POT (Python Optimal Transport):** For the Sinkhorn algorithm.
*   **Matplotlib:** For plotting.
*   **Seaborn:** For enhanced plotting.
*   **Pandas:** For data manipulation and display.

You can install these libraries using pip:
```bash
pip install numpy pot matplotlib seaborn pandas jupyter
