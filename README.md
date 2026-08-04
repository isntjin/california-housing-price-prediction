# california-housing-price-prediction

A first end-to-end machine learning project predicting median house values in California census districts from demographic and geographic features, using linear regression.

## Overview
Used California Housing dataset to predict the median house value of a district from features like median income, house age, and location. I explored the data, built a linear regression baseline, then improved on it with a random forest, and used cross-validation to get an honest estimate of performance. The random forest raised R² from ~0.58 to ~0.80 by capturing the non-linear relationships a straight line can't.

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
- Validation: Used 5-fold cross-validation to check the results weren't an artifact of one lucky split

## Results
Linear Regression = 0.576: Baseline. Limited by its straight-line assumption.
Random Forest = 0.805: T	Captures non-linear relationships.
Random Forest (5-fold CV): 	Shuffled cross-validation. the most trustworthy estimate.

## Key Takeaways
- Median income is the dominant driver of house value in this data.
- The relationships are non-linear, so the random forest clearly beats linear regression.
- How you validate matters: unshuffled cross-validation on ordered data can understate performance. Shuffling gives a fairer estimate.

## How to Run
Open california_housing_price_prediction.ipynb in Google Colab or Jupyter.
Run all cells top to bottom. The dataset loads automatically via scikit-learn — no manual download needed.

Requirements: numpy, pandas, matplotlib, scikit-learn
