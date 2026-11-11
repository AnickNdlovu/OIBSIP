dups_removed = rows_before - len(df)
best = results_df.sort_values('R2', ascending=False).iloc[0]
age_corr = df['selling_price'].corr(df['car_age'])
fuel_med = df.groupby('fuel')['selling_price'].median().sort_values(ascending=False)

table = "\n".join(
    f"| {r.Model} | {r.MAE:,.0f} | {r.RMSE:,.0f} | {r.R2:.3f} |"
    for r in results_df.itertuples()
)
if hasattr(best_model, 'feature_importances_'):
    top3 = pd.Series(best_model.feature_importances_, index=X.columns).sort_values(ascending=False).head(3)
    top3_text = ", ".join(f"{n} ({v:.0%})" for n, v in top3.items())
else:
    top3_text = "see the feature importance chart"

insights = f"""- Cleaning: removed {dups_removed} duplicate rows and standardised the text in the categorical columns (for example, different capitalisation of fuel types).
- Car age has a correlation of {age_corr:.2f} with selling price, so older cars sell for less.
- Median selling price by fuel type: {", ".join(f"{k} {v:,.0f}" for k, v in fuel_med.items())} (rupees).
- Best model: {best.Model} (R² {best.R2:.3f}, MAE {best.MAE:,.0f}, RMSE {best.RMSE:,.0f}).
- Most important features in the best model: {top3_text}."""

readme = f"""# Car Price Prediction with Machine Learning

**Oasis Infobyte Data Science Internship | Task 3**

## Objective
Build regression models that predict the selling price of a used car from features such as brand, age, kilometres driven, fuel type, seller type, transmission and owner history.

## Dataset
CarDekho used car listings from Kaggle ("Vehicle dataset"): {len(df)} cars after cleaning.

## Steps
1. Loaded the data and checked data types, missing values and duplicates
2. Cleaned the data: removed {dups_removed} duplicate rows and fixed inconsistent text values
3. Engineered features: car age (from the year column) and brand (from the car name)
4. Explored price distribution, price by fuel type and price against car age
5. One-hot encoded the categorical variables and built a correlation heatmap
6. Split the data 80/20 and trained Linear Regression, Random Forest and Gradient Boosting
7. Evaluated the models with MAE, RMSE and R², and charted feature importance for the best one

## Results
| Model | MAE | RMSE | R² |
|---|---|---|---|
{table}

## Key Insights
{insights}

## How to Run
1. Install the libraries: `pip3 install pandas numpy matplotlib seaborn scikit-learn jupyter`
2. Open `car_price_prediction.ipynb` in VS Code or Jupyter
3. Click Run All

## Screenshots
See the `screenshots` folder.
"""

print("===== OBSERVATIONS (paste into a Markdown cell at the end of the notebook) =====")
print(insights)
print()
print("===== README (paste into README.md) =====")
print(readme)