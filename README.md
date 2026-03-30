# Market Impact Modeling & Financial Data Analysis

A comprehensive analysis of temporary price impact in financial markets using advanced machine learning techniques and order book data.

## 🎯 Project Overview

This project implements a sophisticated two-stage approach to model temporary price impact in financial markets using the formula:

```
gt = αt × x^γ
```

Where:
- `gt` = temporary price impact (slippage)
- `αt` = dynamic impact coefficient
- `x` = trade size
- `γ` = universal shape parameter

## 📊 Key Features

- **Multi-Ticker Analysis**: Processes data from multiple financial instruments (CRWV, FROG, SOUN)
- **Advanced Feature Engineering**: Extracts 15+ features from order book data including spread, imbalance, bid/ask ratios
- **Two-Stage Modeling**: Novel approach separating universal shape from dynamic market conditions
- **High Performance**: Achieves R² scores of **95.71%** for impact coefficient prediction and **82.77%** for total slippage

## 🏗️ Architecture

### Stage 1: Universal Shape Parameter (γ)
- Uses linear regression on log-transformed data
- Finds the fundamental concavity of impact curves
- Results in γ ≈ 0.1979 across all market conditions

### Stage 2: Dynamic Impact Modeling (αt)
- Employs LightGBM with hyperparameter optimization
- Predicts market-condition-dependent impact levels
- Uses comprehensive feature set from order book dynamics

## 📁 File Structure

```
├── README.md                           # Project documentation
├── market_impact_2.ipynb              # Main analysis notebook (1.7MB)
├── ticker_3_preprocess_load.ipynb     # Data preprocessing pipeline
├── shuffled_df.csv                    # Processed dataset (7.2MB)
├── task_2.pdf                         # Project specifications
└── Impact_function.pdf                # Theoretical background
```

## 🔧 Technical Implementation

### Data Processing Pipeline
1. **Data Extraction**: Unzips and processes raw market data files
2. **Feature Engineering**: Computes market microstructure indicators
3. **Minute Aggregation**: Converts tick data to minute-level snapshots
4. **Simulation**: Generates synthetic trading scenarios

### Key Features Engineered
- **Spread & Mid-Price**: Basic price metrics
- **Order Book Imbalance**: Bid/ask size ratios
- **Cumulative Sizes**: Total liquidity at top levels
- **Price Slopes**: Order book depth characteristics
- **Temporal Features**: Time-based cyclical patterns
- **Asymmetry Metrics**: Market structure imbalances

### Model Performance
- **Training Samples**: 17,719
- **Test Samples**: 4,430
- **Final Dataset**: 22,149 observations
- **Cross-Validation**: 3-fold with hyperparameter tuning

## 📈 Results

| Metric | Score |
|--------|-------|
| Log(α) Prediction R² | **95.71%** |
| Total Slippage R² | **82.77%** |
| Shape Parameter (γ) | **0.1979** |

## 🛠️ Technologies Used

- **Python 3.x**
- **pandas** & **numpy** - Data manipulation
- **LightGBM** - Gradient boosting
- **scikit-learn** - Machine learning pipeline
- **matplotlib** & **seaborn** - Visualization
- **tqdm** - Progress tracking

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy lightgbm scikit-learn matplotlib seaborn tqdm
```

### Running the Analysis
1. **Data Preprocessing**:
   ```bash
   jupyter notebook ticker_3_preprocess_load.ipynb
   ```

2. **Main Analysis**:
   ```bash
   jupyter notebook market_impact_2.ipynb
   ```

## 📖 Methodology

### Two-Stage Approach Benefits
1. **Universality**: Shape parameter remains consistent across market conditions
2. **Adaptability**: Impact level adjusts to current liquidity conditions
3. **Interpretability**: Clear separation of structural vs. temporal effects
4. **Robustness**: Reduces overfitting through principled decomposition

### Feature Selection Strategy
- Order book depth characteristics
- Temporal market patterns
- Liquidity asymmetry measures
- Price movement indicators

## 🎓 Academic Context

This work builds upon established market microstructure theory and contributes:
- Novel two-stage decomposition of impact functions
- Comprehensive feature engineering from order book data
- Empirical validation across multiple financial instruments

## 👨‍💻 Author

**Ajit Priyadarshi**
- AI Engineer | Data Scientist
- IIT-BHU (Varanasi)
- [LinkedIn](https://linkedin.com/in/ajit-priyadarshi-395958227)
- [GitHub](https://github.com/Z-Sigma)

## Note

This project is part of an academic assessment. Please respect intellectual property rights.
