# Lab 3: Monte Carlo Methods in Blackjack
**MSDS 684: Reinforcement Learning | Regis University**

## Project Overview
This project implements **On-Policy First-Visit Monte Carlo (MC) Control** to solve the `Blackjack-v1` environment. Unlike model-based approaches (Dynamic Programming), MC methods learn optimal strategies directly from experience through episode sampling.



## Core Features
- **Experience-Based Learning:** Implementation of the First-Visit MC algorithm to estimate $Q(s, a)$.
- **Exploration Strategy:** Utilization of an $\epsilon$-soft policy ($\epsilon=0.1$) to balance the exploration-exploitation trade-off.
- **Large-Scale Training:** The agent was trained over **500,000 episodes** to ensure convergence and variance reduction.
- **3D Visualizations:** State-value functions ($V$) visualized as 3D surfaces for both usable and non-usable ace scenarios.

## Mathematical Foundation
The agent learns by calculating the **Return ($G_t$)**, the total accumulated reward from time $t$:
$$G_t = \sum_{k=0}^{T-t-1} \gamma^k R_{t+k+1}$$

To ensure all actions are explored, we use the **$\epsilon$-soft** update rule:
$$\pi(a|s) = \frac{\epsilon}{|A|} \text{ for non-greedy actions}$$

## Results & Analysis

### Value Function Surfaces
The following 3D plots represent the learned value of the player's hand relative to the dealer's visible card.

| Usable Ace | No Usable Ace |
| :---: | :---: |
| ![Usable Ace](Usable%20Ace.png) | ![No Usable Ace](No%20Usable%20Ace.png) |

### Learning Performance
The learning curve below shows the rolling average reward over the 500k episodes. The upward trend demonstrates the agent successfully optimizing its strategy toward "Basic Strategy" thresholds.

![Learning Curve](Learning%20curve.png)

## Repository Structure
- `Kakashapati_Barsha_Lab3-.ipynb`: The primary Jupyter Notebook containing the training loop and plotting logic.
- `Kakshapati_Barsha_Lab3 Report.pdf`: The formal APA-style lab report.
- `requirements.txt`: Python dependencies (Gymnasium, NumPy, Matplotlib).
- `/*.png`: Visual deliverables for the README.

## References
Sutton, R. S., & Barto, A. G. (2018). *Reinforcement Learning: An Introduction* (2nd ed.). MIT Press.
