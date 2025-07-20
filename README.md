# Optimal_Trading_Portfolio_from_mutual_funds

# 📈 Optimal Trading Portfolio from Mutual Funds

This project demonstrates how to construct an optimal investment portfolio from mutual funds using **Modern Portfolio Theory (MPT)** and the **Riskfolio-Lib** Python library. It covers the entire workflow — from data cleaning to simulation and optimization — using real-world mutual fund data.

---

## 🧠 Objective

- **Simulate** portfolio performance under varying market conditions
- **Optimize** fund allocation for the highest risk-adjusted return
- **Visualize** efficient frontiers and risk-return tradeoffs

We apply the **Mean-Variance Optimization (MVO)** framework and assume log returns follow a multivariate **Normal Distribution**:

> $$ R \sim \mathcal{N}(\mu, \Sigma) $$

Where:
- \( \mu \) = mean vector of historical log returns
- \( \Sigma \) = covariance matrix of returns

---

## 📂 Project Structure

| Section | Description |
|---------|-------------|
| 📊 Data Preparation | Load & clean mutual fund price data |
| 📈 Return Calculation | Compute log returns using $$ r_t = \log\left(\frac{P_t}{P_{t-1}}\right) $$ |
| 🔍 Exploratory Analysis | Visualize correlation matrix, risk-return profiles |
| 📌 Optimization | Maximize Sharpe Ratio using Riskfolio-Lib |
| 🔁 Monte Carlo Simulation | Generate synthetic return paths |
| ⚡ Efficient Frontier | Visualize optimal portfolios under MPT |

---

## 🧰 Libraries Used

- `numpy`, `pandas`, `matplotlib`, `seaborn`
- `cvxpy`, `scipy`
- [`riskfolio-lib`](https://riskfolio-lib.readthedocs.io/en/latest/)

---

## 📈 Portfolio Optimization Logic

### ✔️ Goal

Maximize the **Sharpe Ratio**:

$$
\text{Sharpe Ratio} = \frac{E(R_p) - R_f}{\sigma_p}
$$

Subject to:
- Weight constraints (e.g. no short-selling)
- Risk or return targets
- Sector or asset allocation bounds (if needed)

### ✔️ Model Formulation

$$
\begin{align*}
\text{Maximize} \quad & \frac{R(w) - r_f}{\sqrt{w^T \Sigma w}} \\
\text{Subject to} \quad & A \cdot w \geq B \\
                       & \sum w_i = 1 \quad \text{(fully invested)}
\end{align*}
$$

---

## 🛠️ Installation & Setup

Use the following setup to ensure compatibility (especially on Kaggle/Colab):

```bash
!pip install --force-reinstall --no-deps --ignore-installed numpy==1.23.5
!pip install --force-reinstall --no-cache-dir scipy==1.10.1
!pip install --force-reinstall --no-cache-dir cvxpy==1.2.0
!pip install --force-reinstall --no-cache-dir riskfolio-lib==6.3.1
