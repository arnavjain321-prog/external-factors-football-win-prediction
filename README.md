Weather & Match Conditions – Predicting Home Win Probability (Machine Learning Analysis)
Executive Summary

This project builds a logistic regression model to estimate home win probability using weather, travel distance, and bookmaker expectations.
By pairing structured match-level features with interaction-effect visualizations, the analysis reveals how external conditions influence match outcomes beyond typical team-strength indicators.

The goal is to demonstrate a modern analytics workflow—including feature engineering, model evaluation, calibration, and counterfactual heatmaps—while providing interpretable insights relevant to football performance analysis and predictive modeling departments.

1. Why This Analysis Matters

Match performance is influenced by more than tactics and lineups.
Environmental and logistical factors meaningfully shape outcomes through:

Physical strain from travel demands

Reduced efficiency under extreme temperature/humidity

Discrepancies between bookmaker expectations and actual conditions

Match tempo and fatigue patterns affected by weather

This project investigates how these factors interact and provides a structured framework for incorporating them into predictive pipelines.

2. Data Sources

Match-level data containing results and bookmaker implied probabilities

Weather data merged by match location and date

Travel distance computed from team origin → stadium

Target variable: home win (1) or non-win (0)

All processed tables are stored inside the data/ directory.

3. Repository Structure
EXTERNAL-FACTORS-FOOTBALL-MODELING/
│
├── data/
│   ├── processed/
│   │   └── matches_modeling_dataset.csv
│   │
│   └── raw/
│       ├── 1_venue.csv
│       ├── 5_odds.csv
│       ├── leagues_more.csv
│       └── weather_output.csv
│
├── notebooks/
│   ├── 01_data_processing.ipynb
│   ├── 02_modeling.ipynb
│   └── 03_reporting.ipynb
│
├── visuals/
│   ├── calibration_curve_gradient_boosting.png
│   ├── calibration_curve_logistic_regression.png
│   ├── confusion_matrix_catboost.png
│   ├── confusion_matrix_gradient_boosting.png
│   ├── confusion_matrix_logistic_regression.png
│   ├── confusion_matrix_random_forest.png
│   ├── feature_importance_std_effects.png
│   ├── interaction_temp_humidity.png
│   ├── interaction_travel_bookmaker.png
│   ├── pdp_attendance_ratio.png
│   ├── pdp_humidity.png
│   ├── pdp_p_home_implied.png
│   ├── pdp_temp.png
│   ├── pdp_travel_km.png
│   ├── pdp_windspeed.png
│   ├── roc_curve_logistic_regression.png
│   └── roc_curves_all_models.png
│
├── .gitignore
├── LICENSE
└── README.md


Notebook Workflow

01_clean_data.ipynb – Raw data import + merging
02_feature_engineering.ipynb – Per-match & contextual features
03_model_training.ipynb – Logistic regression + CV
04_evaluation.ipynb – ROC, calibration, confusion matrix
05_interaction_effects.ipynb – Counterfactual heatmaps

4. Modeling Overview

The predictive pipeline includes:

Logistic Regression (selected as best-performing model)

Standardization of continuous features

Cross-validation for regularization strength

Probability calibration evaluation

Interaction effects via controlled variable grids

Features Used

Weather Variables

Temperature

Humidity

Category-based weather indicators

Context & Expectation Variables

Bookmaker implied probability

Home/away flags

Travel Variables

Travel distance (km)

Interaction: travel × bookmaker probability

5. Visualizations

Below is a summary of the primary visuals included in the analysis:

Model Diagnostics

Confusion Matrix

ROC Curve

Calibration Curve

Standardized Feature Importance

Interaction Effects

Temperature × Humidity
Visualizes how combined environmental conditions modify home win probability under typical match settings.

Travel Distance × Bookmaker Implied Probability
Evaluates how travel burden interacts with market expectations.

These figures are stored in visuals/.

6. Key Insights

1. Environmental conditions influence performance.
High humidity and extreme temperature depress predicted win probability even when controlling for team strength.

2. Travel distance consistently penalizes outcomes.
Teams facing longer travel show lower predicted likelihood of winning at home.

3. Bookmaker probabilities are strong predictors but incomplete.
The model identifies several matches where weather or logistical factors shift actual probabilities away from implied odds.

4. Interaction effects reveal compound disadvantages.
Weather and travel effects are not independent—certain combinations cause sharp declines in modeled win probability.

7. Limitations & Future Work

Integrating player availability and lineup-specific metrics

Adding expected-goal differential or underlying performance data

Testing non-linear models (random forest, XGBoost)

Deploying the probability model via a lightweight API

8. License

This project is released under the MIT License.

9. Author

Arnav Jain
Master’s in Data Science (University of Virginia)
LinkedIn: https://www.linkedin.com/in/arnavjain2026