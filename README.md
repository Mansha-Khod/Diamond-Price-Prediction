# Diamond Price Prediction — Multi-Model Regression Analysis in R

A rigorous regression study comparing **7 statistical models** on the classic diamonds dataset (53,940 records), with a complete end-to-end pipeline from data cleaning to held-out test evaluation.

---

## Project Highlights

- **Best model:** MAPE of **2.50%** and R² of **0.948** on a held-out test set of 9,503 records
- **7 models compared:** Simple Linear Regression, Multiple Linear Regression, Ridge, Lasso, Forward Stepwise, Backward Stepwise, and Stepwise Selection
- **Full statistical pipeline** — outlier removal, multicollinearity checks, transformation, stratified splitting, and multi-metric evaluation

---

## Methodology

### 1. Data Cleaning & Outlier Removal
- Applied **IQR-based** outlier removal as an initial pass
- Used **Cook's Distance** to identify and remove high-influence observations — this alone lifted R² noticeably
- Result: cleaner residuals and improved model generalisability

### 2. Feature Engineering & Transformation
- Applied **log transformation** on the target variable (`price`) to correct right skew and stabilise variance
- Encoded categorical features (`cut`, `color`, `clarity`) appropriately

### 3. Multicollinearity Check
- Computed **Variance Inflation Factors (VIF)** to detect and handle multicollinearity among predictors (`x`, `y`, `z`, `carat`)

### 4. Train-Test Split
- **80/20 stratified split** — 44,437 training records, 9,503 test records
- Stratification ensured representative distribution of price ranges

### 5. Model Training & Comparison
| Model | Description |
|-------|-------------|
| SLR | Single predictor baseline |
| MLR | All predictors |
| Ridge | L2 regularisation |
| Lasso | L1 regularisation + feature selection |
| Forward Stepwise | Builds up from null model |
| Backward Stepwise | Prunes from full model |
| Stepwise | Bidirectional selection |

### 6. Evaluation Metrics
All models evaluated on the held-out test set using:
- **R²** — proportion of variance explained
- **RMSE** — root mean squared error
- **MAE** — mean absolute error
- **MAPE** — mean absolute percentage error *(primary metric)*

---

## Results Summary

| Model | R² | MAPE |
|-------|----|------|
| Best model (post Cook's Distance) | **0.948** | **2.50%** |

---

##  Files

```
diamond-price-prediction/
├── Linear_Regression_On_a_Diamond_Dataset.R   # Full analysis script
└── README.md
```

---

## Tech Stack

- **Language:** R
- **Key techniques:** OLS Regression, Ridge, Lasso, Stepwise Selection, Cook's Distance, VIF, Log Transformation

---

## Dataset

The **diamonds** dataset from the `ggplot2` package — 53,940 round-cut diamonds with 10 features including carat, cut, color, clarity, and price.

---

## How to Run

1. Open `Linear_Regression_On_a_Diamond_Dataset.R` in RStudio
2. Install required packages if prompted (`ggplot2`, `MASS`, `glmnet`, `car`)
3. Run the script top to bottom — outputs include model summaries, VIF tables, and evaluation metrics
