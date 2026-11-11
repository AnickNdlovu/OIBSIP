# Sales Prediction Using Python

**Oasis Infobyte Data Science Internship | Task 5**

## Objective
Build regression models that predict product sales from advertising spend on TV, Radio and Newspaper.

## Dataset
Advertising.csv: 200 rows, 3 advertising channels (TV, Radio, Newspaper) and Sales. There are no missing values.

## Steps
1. Loaded the data, removed an extra index column and ran EDA (nulls, descriptive statistics)
2. Plotted Sales against each channel and built a correlation heatmap
3. Split the data 80/20
4. Trained Linear Regression (baseline) and Random Forest Regressor
5. Evaluated both with MAE, RMSE and R²
6. Plotted the residuals of the best model
7. Interpreted which channel has the biggest impact

## Results
| Model | MAE | RMSE | R² |
|---|---|---|---|
| Linear Regression | 1.461 | 1.782 | 0.899 |
| Random Forest | 0.619 | 0.766 | 0.981 |

## Key Insights
- Random Forest is the best model (R² 0.981). The Linear Regression residuals form a U-shape, so the relationship is not purely linear.
- TV has the strongest correlation with Sales (0.782), followed by Radio (0.576).
- In the Random Forest, TV accounts for about 62% of the feature importance, Radio about 36% and Newspaper about 1%.
- Newspaper correlates weakly with Sales (0.23), partly because it correlates with Radio (0.35). Once Radio is in the model, its own effect is close to zero.
- A business with a limited budget should prioritise TV and Radio.

## How to Run
1. Install the libraries: `pip3 install pandas numpy matplotlib seaborn scikit-learn jupyter`
2. Open `sales_prediction.ipynb` in VS Code or Jupyter
3. Click Run All

## Screenshots
See the `screenshots` folder.