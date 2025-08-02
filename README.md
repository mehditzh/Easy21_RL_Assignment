# Reinforcement Learning Assignment – Easy21

This repository contains my implementation of the Easy21 assignment from the **2015 UCL Reinforcement Learning (COMPM050/COMPGI13)** course taught by **David Silver**.

- 📄 [Assignment PDF](https://davidstarsilver.wordpress.com/wp-content/uploads/2025/04/easy21-assignment.pdf)  
- 🌐 [Course Website](https://davidstarsilver.wordpress.com/teaching/)
- 💻 'All in One' Notebook: [`easy21_assignment.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/0-easy21_assignment.py)

---

## 📁 Repository Structure

Five Python files are included:

- [`easy21_env.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/1-easy21_env.py): Defines the Easy21 environment.
- [`easy21_MonteCarlo.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/2-easy21_montecarlo.py): Solves the environment using Monte Carlo control.
- [`easy21_Sarsa.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/3-easy21_sarsa.py): Implements the TD learning (SARSA(λ)) algorithm.
- [`easy21_FN_approximation.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/4-easy21_fn_approximation.py): Uses linear function approximation with SARSA(λ).
- [`easy21_assignment.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/0-easy21_assignment.py): A combined notebook executing all steps sequentially.

---

## ▶️ How to Run the Code

### Option 1 – Run Everything Sequentially
Simply execute the notebook/script `easy21_assignment.py` cell by cell.

### Option 2 – Run Each Part Individually
If you want to run each component independently (useful for debugging), follow these steps:

1. **Run `easy21_env.py`** and save the file locally.
2. **Run `easy21_MonteCarlo.py`**:
   - Upload `easy21_env.py`.
   - Run the script.
   - Save the output file: `MC_values.npy`.
3. **Run `easy21_Sarsa.py`**:
   - Upload both `easy21_env.py` and `MC_values.npy`.
   - Run the script.
4. **Run `easy21_FN_approximation.py`**:
   - Same steps as SARSA.

---

##  1. Easy21 Environment

💻 [`easy21_env.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/1-easy21_env.py)

This file sets up the Easy21 game environment as described in the assignment. It defines the card drawing mechanism, game dynamics, and state-action spaces.

---

##  2. Monte Carlo Control in Easy21

💻 [`easy21_MonteCarlo.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/2-easy21_montecarlo.py)

- Runs Monte Carlo control for **20 million episodes**.
- Explores different levels of exploration by changing the `N0` parameter.
- The resulting value matrix is reused as ground truth in later parts.

#### 📊 Value Function Visualizations

<table>
  <tr>
    <td><b>Non-Greedy<br>(Random Policy)</b></td> 
    <td>
      <img src="https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Plots/2.%20Monte%20Carlo%20Plots/MonteCarlo.NonGreedy.jpg?raw=true" height="200" width="280"/>
    </td>
    <td><b>N₀ = 500</b></td> 
    <td>
      <img src="https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Plots/2.%20Monte%20Carlo%20Plots/MonteCarlo.N0500Greedy.jpg?raw=true" height="200" width="280"/>
    </td>
  </tr>
  <tr>
    <td><b>N₀ = 100<br>(Assignment Default)</b></td> 
    <td>
      <img src="https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Plots/2.%20Monte%20Carlo%20Plots/MonteCarlo.N0100Greedy.jpg?raw=true" height="200" width="280"/>
    </td>
    <td><b>Greedy</b></td>
    <td>
      <img src="https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Plots/2.%20Monte%20Carlo%20Plots/MonteCarlo.Greedy.jpg?raw=true" height="200" width="280"/>
    </td>
  </tr>
</table>

---

##  3. TD Learning in Easy21 (SARSA(λ))

💻 [`easy21_Sarsa.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/3-easy21_sarsa.py)

- Implements SARSA(λ) for values of λ in `{0, 0.1, ..., 1.0}`.
- Each configuration is run **10,000 episodes**.
  
#### 📊 Plots:
- Learning curves for λ = 0 and λ = 1.
![Learning Curves](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Plots/3.%20Sarsa%20Plots/Sarsa.Leaning_Curves.png)
- MSE vs. λ graph.
![MSE vs. λ](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Plots/3.%20Sarsa%20Plots/Sarsa.MSE_vs_Lambda.png)

*Observation*: Despite several runs, λ = 1 consistently resulted in poor performance (highest MSE in most cases).

---

##  4. Function Approximation in Easy21

💻 [`easy21_FN_approximation.py`](https://github.com/mehditzh/Easy21_RL_Assignment/blob/main/Notebooks/4-easy21_fn_approximation.py)

- Uses **linear function approximation** with SARSA(λ).
- Same episode count and λ values as the TD Learning section.

#### 📊 Plots:
- Learning curves for λ = 0 and λ = 1.
- MSE vs. λ.

*Observation*: The MSE started surprisingly low and remained inconsistent for λ = 1. Despite reviewing the code thoroughly, the reason for this discrepancy compared to other online solutions remains unclear.



