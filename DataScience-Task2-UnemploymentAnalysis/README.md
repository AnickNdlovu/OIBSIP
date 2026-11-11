# Unemployment Analysis with Python

**Oasis Infobyte Data Science Internship | Task 2**

## Objective
Explore unemployment data for Indian states to find regional and monthly trends, with a focus on the impact of the COVID-19 lockdown.

## Dataset
"Unemployment in India" from Kaggle: monthly unemployment rate, number employed and labour participation rate for each state, from May 2019 to June 2020.

## Steps
1. Loaded the data, cleaned column names and converted Date to a datetime type
2. Found and dropped 28 completely empty rows
3. Calculated region-wise averages and monthly trends
4. Plotted unemployment over time for Maharashtra, Delhi, Tamil Nadu and Kerala
5. Charted the top 10 states by average unemployment rate
6. Built a correlation heatmap of unemployment rate, employment and labour participation
7. Compared pre-COVID and post-COVID periods, using the start of the national lockdown (25 March 2020) as the cut-off

## Key Findings
- The average unemployment rate rose from 9.51% before the lockdown to 17.77% after it.
- The average number employed fell from about 7.47 million to 6.52 million.
- Tamil Nadu peaked at about 49% in May 2020, while Delhi and Kerala peaked in June.
- Tripura and Haryana have the highest average unemployment rates across the whole period.
- Labour participation shows almost no linear correlation with the unemployment rate or the number employed.

## Limitations
- The post-COVID period covers only about three months (April to June 2020), against about ten before it, so the comparison is a snapshot, not a long-term trend.
- The data ends in June 2020, so the recovery cannot be assessed.

## How to Run
1. Install the libraries: `pip3 install pandas numpy matplotlib seaborn jupyter`
2. Open `unemployment_analysis.ipynb` in VS Code or Jupyter
3. Click Run All

## Screenshots
See the `screenshots` folder.