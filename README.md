# 🔬 Spurious Correlation Monte Carlo Simulation

### An Investigation into Type I Error Rates in High-Dimensional Data Analysis

This repository hosts an advanced Monte Carlo simulation study focusing on the fundamental statistical challenge of **Spurious Correlation** and the quantification of **Type I Error** rates in large-scale testing.

[![GitHub Stars](https://img.shields.io/github/stars/wajason/ISLR-Ch4-Classification-Labs?style=for-the-badge&logo=github&color=6699CC)](https://github.com/wajason/ISLR-Ch4-Classification-Labs/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/wajason/ISLR-Ch4-Classification-Labs?style=for-the-badge&logo=github&color=6699CC)](https://github.com/wajason/ISLR-Ch4-Classification-Labs/network/members)
[![Issues](https://img.shields.io/github/issues/wajason/ISLR-Ch4-Classification-Labs?style=for-the-badge&logo=github&color=6699CC)](https://github.com/wajason/ISLR-Ch4-Classification-Labs/issues)
[![License](https://img.shields.io/badge/License-MIT-6699CC?style=for-the-badge)](./LICENSE)

## 🌟 Project Objective

This project utilizes a **Monte Carlo simulation**  to address a critical statistical concern: the likelihood of observing strong, high-magnitude correlations ($\mathbf{|r|}$) between variables that are mathematically independent ($\rho=0$). [cite_start]The work focuses on quantifying the frequency of **Spurious Correlation** and the resulting **Type I Error** when performing large-scale correlation sweeps.

## 🚀 Methodology and Setup

[cite_start]The analysis is based on $\mathbf{N=10,000}$ iterations [cite: 22] [cite_start]to empirically derive the sampling distribution of the Pearson correlation coefficient ($r$) under the strict null hypothesis[cite: 20, 28].

| Metric (指標) | Value (數值) | Rationale (理由/目的) |
| :--- | :--- | :--- |
| **I. 模擬參數 (Numerical Parameters)** | | |
| **Total Simulations (N)** (總模擬次數) | 10,000 | [cite_start]Robust sample size for empirically deriving the sampling distribution of $r$[cite: 78, 28]. |
| **Sample Size (n)** (每組樣本數) | 50 | [cite_start]Represents the number of observations used for each correlation test in the simulation[cite: 36, 37, 21]. |
| **Significance Threshold ($r_{\text{crit}}$)** (臨界值) | 0.279 ($\alpha=0.05$) | [cite_start]The critical value for rejecting $\mathbf{\rho=0}$ derived from the t-distribution for $\mathbf{n=50}$[cite: 52, 54, 57]. |
| **II. 環境與假設 (Assumptions & Tools)** | | |
| **Variables** (變數設定) | $Y \sim \mathcal{N}(0,1)$; $X_i \sim \mathcal{N}(0,1)$ | **Fundamental Assumption:** Ensures variables are I.I.D. (Independent and Identically Distributed)[cite_start], guaranteeing zero true population correlation ($\rho=0$)[cite: 13, 22]. |
| **Tools** (分析工具) | R (Quarto, ggplot2, gt, patchwork) | Utilized for reproducible reporting, advanced statistical visualization, and professional table formatting. |

| Correlation Strength Threshold | Count (N=10,000) | Probability (%) | Interpretation |
| :--- | :--- | :--- | :--- |
| **$|r| > 0.5$ (Very Strong)** | **5** | **0.05%** | [cite_start]**Extremely Rare:** Represents the highest risk of false discovery[cite: 250, 314]. |
| **$|r| > 0.4$ (Strong)** | **39** | **0.39%** | [cite_start]**Rare:** High-magnitude errors that can mislead conclusions[cite: 250, 314]. |
| **$|r| > r_{\text{crit}}$ (Significant)** | 463 | 4.63% | [cite_start]Total Type I Error rate (close to the theoretical 5% boundary)[cite: 86, 313]. |

## 🎯 Core Findings and Quantification of Error

The simulation definitively confirms that high-magnitude spurious correlations are an **inevitable consequence** of high-dimensional testing.

### 1. Quantification of Extreme Spurious Correlation

The analysis specifically targets correlations strong enough to be considered substantively meaningful ($|r| > 0.4$ and $|r| > 0.5$).

| Correlation Strength Threshold | Count (N=10,000) | Probability (%) | Interpretation |
| :--- | :--- | :--- | :--- |
| **$|r| > 0.5$ (Very Strong)** | **5** | **0.05%** | **Extremely Rare:** Represents the highest risk of false discovery. |
| **$|r| > 0.4$ (Strong)** | **39** | **0.39%** | **Rare:** High-magnitude errors that can mislead conclusions. |
| **$|r| > r_{\text{crit}}$ (Significant)** | 463 | 4.63% | Total Type I Error rate (close to the theoretical 5% boundary). |

### 2. Visual Interpretation of Distribution (Empirical vs. Theoretical)

The final report includes a color-coded histogram that visually emphasizes the probability of these events.

* **Symmetry:** The $r$ distribution is symmetric and centered around zero, confirming the independence of the underlying variables.
* **Rarity:** The rapid decline of the density curve indicates that observing a high-strength correlation ($|r|$) is low.
* **Extreme Tails:** The color segmentation confirms that only a minute number of trials result in correlations exceeding the high thresholds of $|r|>0.4$ or $|r|>0.5$.

## 🔗 Project Conclusion and Future Work

The results underscore the essential statistical principle that **p-values and correlation coefficients lose their reliability when massive multiple comparisons are performed without correction**. Even with I.I.D. data, the sheer number of tests ensures that a certain number of random coincidences will appear highly significant.

For researchers engaging in exploratory data analysis (EDA) or feature selection in large datasets, this simulation serves as a critical warning against the dangers of **data dredging**.

***
