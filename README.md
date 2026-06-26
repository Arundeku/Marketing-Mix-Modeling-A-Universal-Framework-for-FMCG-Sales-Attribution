# Marketing Mix Modeling: A Universal Framework for FMCG Sales Attribution

## Project Overview
This repository contains a three-stage, end-to-end analytical framework designed to solve one of the most persistent challenges in the Fast-Moving Consumer Goods (FMCG) sector: accurately attributing sales to simultaneous marketing channels. Moving beyond basic proprietary tools, this project provides an independent, model-driven pipeline that ingests raw sales data, autonomously trains predictive models, and outputs mathematically grounded contribution percentages for media budget optimization. 

## Core Architecture & Modules

### 1. Universal Data Cleaning Pipeline
Real-world retail data is rarely model-ready. This module serves as an automated preprocessing engine:
* Automatically detects file encoding and standardizes formats.
* Handles mixed data types, such as isolating and nullifying string errors (e.g., 'ERROR' or 'UNKNOWN') hidden within numeric revenue columns.
* Executes type-aware imputation, applying median values for skewed numeric features and mode values for categorical gaps.

### 2. Autonomous AI-Driven ML Modeling Pipeline
An intelligent predictive engine that iteratively optimizes itself without manual intervention:
* Integrates a Large Language Model as a decision agent to analyze dataset intelligence (skewness, cardinality, correlations) and recommend starting architectures.
* Autonomously executes dynamic feature engineering, including cyclical date transformations, target encoding, and the generation of interaction terms.
* Evaluates results and iterates through hyperparameter tuning and ensembling, ultimately achieving a final ensemble (XGBoost + Random Forest) test R-squared of 0.8724.
* Identifies granular sales drivers, revealing that stock availability and SKU interaction terms outweigh baseline marketing features in predicting short-term volume.

### 3. The Marketing Mix Model (MMM) Engine
The core attribution framework that accounts for media carryover and diminishing returns:
* **Transformations:** Applies geometric Adstock ($A_t = E_t + \lambda A_{t-1}$) to model delayed advertising awareness, followed by the Hill Saturation function to capture diminishing returns on ad spend.
* **Multi-Architecture Comparison:** Simultaneously runs seven distinct models (including Lasso, Ridge, Random Forest, XGBoost, OLS, and Bayesian PyMC) to benchmark performance and establish consensus.
* **Solving Multicollinearity:** Demonstrates how unregularized models (like OLS) fail due to highly correlated spend data, while robust architectures (Lasso and Bayesian) successfully isolate true channel impacts.

## Key Business Insights & Strategic Recommendations
This framework translates statistical outputs into actionable product and marketing strategies:
* **Model Reliability:** Lasso emerged as the strongest frequentist architecture (MAPE: 3.07%, R-squared: 0.9726), while the Bayesian PyMC model (MAPE: 3.19%, R-squared: 0.9671) provided crucial uncertainty quantification.
* **Baseline Demand:** Base Sales (driven by distribution and macroeconomics) account for approximately 47% of total revenue, highlighting the necessity of supply chain reliability.
* **Media Reallocation:** TV (~22%) and Facebook (~20%) represent the most reliable paid media drivers, whereas TikTok and Influencer channels exhibited high attribution uncertainty, signaling the need for localized incrementality testing before scaling budgets.

## Tech Stack
* **Languages & Core Libraries:** Python, pandas, NumPy, scikit-learn, statsmodels.
* **Machine Learning & Ensembles:** XGBoost, Random Forest, CatBoost.
* **Probabilistic Programming:** PyMC (Markov Chain Monte Carlo sampling).
* **AI & Automation:** Google Gemini API, Selenium (Browser Automation).
* **Feature Engineering:** category_encoders, Optuna (Hyperparameter Optimization).
