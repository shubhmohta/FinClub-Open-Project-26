# FinClub-Open-Project-26
# Stochastic Term Structure Modeling & Interest Rate Dynamics
**Finance Club Open Project 2026 | Indian Institute of Technology (IIT) Roorkee**

[![Python 3.12](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Quant Finance](https://img.shields.io/badge/Domain-Quantitative_Finance-00524e.svg)]()

A robust quantitative framework for modeling the term structure of interest rates. This repository explores the mathematical trade-offs between model rigidity and out-of-sample predictive accuracy, advancing from single-factor diffusion models to state-of-the-art Affine Jump-Diffusion architectures. 

By applying control theory principles, Riccati ODE solvers, and dynamic state estimation, this project extracts unobservable macroeconomic drivers from raw market yield data.

---

## 👨‍💻 Author
**Shubh Mohta** *B.Tech in Electrical Engineering, IIT Roorkee* * **Enrollment No:** 24115142
* **Codeforces:** [Spazion (Expert)](https://codeforces.com/profile/Spazion)

---

## 📐 Core Architectures Analyzed

This project implements and backtests four distinct stochastic frameworks, exposing the structural limitations of base models and mathematically bridging the gap to real-world market dynamics.

### 1. Base Cox-Ingersoll-Ross (CIR)
The foundational mean-reverting square-root diffusion process:
$$dr_t = \kappa(\theta - r_t)dt + \sigma \sqrt{r_t} dW_t$$
* **Focus:** Demonstrates the Feller boundary (preventing negative rates) and mean-reversion mechanics, while actively exposing the single-factor "spread rigidity" flaw when modeling 10Y-2Y yield curve steepenings.

### 2. Two-Factor CIR 
A multi-factor extension treating the short rate as the sum of independent latent states ($r_t = x_1 + x_2$).
* **Focus:** Grants the model the degrees of freedom required to capture complex curve topologies, successfully predicting yield curve inversions and un-kinking phenomena.

### 3. CIR++ (Brigo-Mercurio Extension)
A deterministic shift augmentation to perfectly calibrate to the initial term structure.
* **Focus:** Utilizes a highly granular Cubic Spline shift function $\Psi(\tau)$ to map structural liquidity and term premiums, bridging the gap between affine physics and precise market pricing.

### 4. Affine Jump-Diffusion (AJD)
An advanced framework integrating discontinuous Poisson jump processes to model sudden macroeconomic shocks (e.g., central bank interventions, flash crashes).
* **Focus:** Analyzes the theoretical "twist" effect of a shock across the curve, demonstrating how the short-end absorbs maximum volatility while the long-end remains anchored by mean-reverting expectations.

---

## ⚙️ Key Methodologies & Tech Stack

* **Dynamic State Extraction:** Implemented high-frequency **Extended Kalman Filtering** to dynamically back out unobservable latent factors ($x_t$) from cross-sectional yield curve shapes.
* **Global Optimization:** Engineered **Differential Evolution** algorithms to navigate non-convex yield surfaces and optimize affine parameters $(\kappa, \theta, \sigma)$ while enforcing strict Feller condition boundaries.
* **Tech Stack:** Python, `NumPy`, `SciPy` (ODE solvers & optimization), `Pandas`, `Matplotlib`, `Seaborn`.

---

## 📊 Visual Diagnostics Pipeline
The notebook features a comprehensive, publication-ready visual diagnostics suite, including:
1. **3D Market Yield Surfaces:** Topographical mapping of the actual out-of-sample term structure evolution.
2. **Residual Heatmaps:** Granular basis-point error tracking across maturities and time.
3. **Latent State Trajectories:** Exposing the invisible macroeconomic drivers ($x_1, x_2$) powering the curve.
4. **Jump Detection & Shock Propagation:** Theoretical plotting of $\pm50$ bps shock propagation and mean-reverting yield curve "twists".

---

## 🚀 Getting Started

### Prerequisites
Ensure you have Python 3.10+ installed. The environment relies heavily on the SciPy ecosystem.

```bash
git clone [https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git)
cd YOUR_REPO_NAME
pip install -r requirements.txt
