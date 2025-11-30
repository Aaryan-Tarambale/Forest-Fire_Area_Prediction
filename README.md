# Forest-Fire_Area_Prediction
This project builds and evaluates machine learning models to predict the burned area of forest fires using meteorological and environmental features.
The dataset contains fire weather indices, temperature, humidity, wind conditions, and spatial attributes. Prediction of burned area is challenging due to heavy zero-inflation, extreme skew, and rare large fires.

## **Project Overview**
1. **Dataset:** Forest Fires dataset from the UCI Machine Learning Repository
2. **Goal**: Predict the continuous burned area (in hectares) based on terrain conditions
3. **Challenges:**
   
   1. 50%+ samples have area = 0
   2. Very few large-fire cases (20–1000 ha)
   3. Strong skew → difficult regression task

Because of this, the focus is on interpretable models, robust evaluation, and understanding model limitations.

## Models Implemented
1. Random Forest Regressor (RF)
  
	1.	Tuned using RandomizedSearchCV
  
	2.	Best performance among all tested models
  
	3. 	Handles noise, non-linearity, and zero-inflated targets well

2. Gradient Boosting Regressor (GBR)
   
	1.	Also tuned using Randomized Search

	2.	Performed slightly worse than RF

	3.	More sensitive to hyperparameters

	4.	Struggled with rare, large-fire events

## Evaluation Metrics
Used metrics appropriate for skewed regression data:

	1.	RMSE (Root Mean Squared Error)
  
	2.	MAE (Mean Absolute Error)
  
	3.	MSE (shown but less interpretable)

## Findings & Observations
	1. 	The model performs well on small fires (0–5 ha)
  
	2. 	It significantly underpredicts large fires, due to lack of training data
  
	3.	Environmental and fire-weather features (temp, DMC, RH, DC, wind) are the strongest predictors
  
	4. 	Temporal/categorical features (month, day) contribute very little

## Futute Scope 
To improve large-fire prediction and overall modeling accuracy:

	1.	Try XGBoost, LightGBM, or CatBoost
  
	2. 	Use a two-step model (classification + regression)
  
	3.	Apply SMOTE or stratified oversampling for large fires
  
	4.	Explore Tweedie, Gamma, or quantile regression
  
	5.	Collect additional data for high-impact fire events
