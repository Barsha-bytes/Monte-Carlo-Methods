# Lab 3: Monte Carlo Methods - Blackjack Optimal Strategy

## 📖 Overview
This project implements **Model-Free Reinforcement Learning** using **Monte Carlo (MC) Methods**. Unlike previous labs that relied on Dynamic Programming and a known environment model ($P$), this implementation learns the optimal strategy for **Blackjack** solely through trial-and-error experience (playing episodes).

##  Key Features
* **Environment:** OpenAI Gymnasium `Blackjack-v1`.
* **Algorithm:** On-Policy $\epsilon$-Greedy Monte Carlo Control.
* **Update Logic:** First-Visit MC to ensure unbiased estimates of the Action-Value function ($Q$).
* **Exploration Strategy:** $\epsilon$-greedy policy with exponential decay to balance exploring new moves and exploiting learned winning strategies.



## The Monte Carlo Approach
Since Blackjack has unknown card probabilities (model-free), we use the **Generalized Policy Iteration (GPI)** framework:
1.  **Policy Evaluation:** We play 500,000 games. For every state visited, we calculate the actual return ($G$) at the end of the game.
2.  **Policy Improvement:** We update our $Q(s, a)$ table using an incremental average:
    $$Q(s, a) \leftarrow Q(s, a) + \frac{1}{N(s, a)} [G - Q(s, a)]$$
3.  **$\epsilon$-Greedy:** We maintain a small probability ($\epsilon$) of taking random actions to ensure we discover all possible winning hands.



##  Results & Visualizations

### 1. Optimal Strategy (Policy Map)
The following map shows the agent's decision-making logic: **Hit vs. Stick**. 
* The x-axis represents the Dealer's visible card.
* The y-axis represents the Player's current sum.



### 2. State-Value Convergence
As the number of episodes increases, the value function stabilizes, showing that staying on a "Hard 20" has a near-certain win value, while hitting on 16 against a Dealer's 7 is high-risk.



