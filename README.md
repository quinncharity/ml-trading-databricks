# ML Trading on Databricks

This repository contains a small, end-to-end workflow for experimenting with **machine learning-based trading strategies** on **Databricks**.  
It is organized around a couple of key notebooks that walk from raw market data and feature engineering through model training and backtesting, with optional experiment tracking.

## Project Structure

- `ml_trading_01_data_and_features.ipynb`

  - Load and clean historical market data
  - Engineer predictive features (e.g. returns, technical indicators, factors)
  - Persist prepared feature tables for downstream modeling

- `ml_trading_02_model_and_backtest.ipynb`

  - Train ML models (e.g. for predicting returns or direction)
  - Evaluate model performance and build basic backtests
  - Analyze strategy metrics (e.g. hit rate, PnL curves, drawdowns)

- `experiments/factor_models_mlflow.py.ipynb`
  - Prototype and compare different factor/feature sets
  - Track experiment metadata and metrics with MLflow (if enabled in your workspace)

You can adapt or extend these notebooks to plug into your own data sources and production pipelines.

## Prerequisites

- A **Databricks workspace** (or a local environment with the Databricks Runtime / `databricks-connect` configured)
- **Python 3.9+** recommended
- Typical Python data/ML libraries, for example:
  - `pandas`, `numpy`
  - `scikit-learn`
  - `matplotlib` or `plotly`
  - `mlflow` (for experiment tracking)

> Note: The exact dependency set will depend on how you extend the notebooks. Install or pin versions according to your environment standards.

## Getting Started

1. **Clone the repository**

   ```bash
   git clone <YOUR-REPO-URL> ml-trading-databricks
   cd ml-trading-databricks
   ```

2. **Create and activate a virtual environment (optional but recommended)**

   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**
   Install the libraries you plan to use (example):

   ```bash
   pip install pandas numpy scikit-learn matplotlib mlflow
   ```

4. **Connect to Databricks**

   - Either upload/import the notebooks into your Databricks workspace and attach them to a cluster
   - Or configure `databricks-connect` locally so that the notebooks can talk to a remote cluster

5. **Run the notebooks**
   - Start with `ml_trading_01_data_and_features.ipynb` to build your feature set
   - Then open `ml_trading_02_model_and_backtest.ipynb` to train models and run backtests
   - Use `experiments/factor_models_mlflow.py.ipynb` for more advanced experimentation and tracking

## Customization Ideas

- Swap in your own **data source** (e.g. Delta tables, Parquet files, or a data warehouse)
- Try different **feature sets** (technical indicators, fundamental signals, alternative data)
- Experiment with **model families** (gradient boosting, random forests, neural networks)
- Enhance the **backtest engine** (transaction costs, slippage, position sizing rules, risk limits)
