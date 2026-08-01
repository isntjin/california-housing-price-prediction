# california-housing-price-prediction

A first end-to-end machine learning project predicting median house values in California census districts from demographic and geographic features, using linear regression.

## Overview
This project uses the California Housing dataset to predict the median house value of a district from features like median income, house age, and location. After exploring the data and checking how each feature correlates with price, I trained a linear regression model and evaluated it on a held-out test set. The model explains roughly 58% of the variation in house values, with a typical prediction error of about $74,500.

## Dataset
- Source: California Housing dataset, via sklearn.datasets.fetch_california_housing (originally derived from the 1990 U.S. Census)
- Rows: 20,640 census districts
- Features (8):
  1. MedInc — median income in the district
  2. HouseAge — median house age
  3. AveRooms — average number of rooms per household
  4. AveBedrms — average number of bedrooms per household
  5. Population — district population
  6. AveOccup — average household occupancy
  7. Latitude / Longitude — district location

## Approach
- Exploration: Reviewed summary statistics, plotted the distribution of median income, and ranked features by their correlation with the target. Median income was by far the strongest positive predictor; latitude and longitude were negatively correlated, reflecting that pricier markets cluster in specific parts of the state.
- Preparation: Split the data into features (X) and target (y), then into an 80/20 train/test split with a fixed random seed for reproducibility.
- Model: Trained a LinearRegression model as a baseline.
- Model Update: Trained a Randomforest to imporove accuracy

## Results
R² = 0.576:	The model explains ~58% of the variation in house values.
RMSE = 0.746	Typical prediction error is ~$74,500 (target is in $100,000s).

## Key Takeaways
- Median income is the dominant driver of house value in this data.
- Location matters and behaves non-linearly, which linear regression struggles to model — a strong hint that a non-linear model would do better.
- Correlation is only a pairwise, linear signal; a low correlation doesn't mean a feature is useless in a model.

## How to Run
Open california_housing_price_prediction.ipynb in Google Colab or Jupyter.
Run all cells top to bottom. The dataset loads automatically via scikit-learn — no manual download needed.
