🇰🇪 Problem Statement: The Kenyan Farmer’s Dilemma
In Kenya, agriculture is the backbone of the economy, yet many smallholder farmers in regions like Uasin Gishu (the breadbasket), Kakamega, and Makueni face declining yields. A major hurdle is the cost of comprehensive soil testing.

While the Kenya Agricultural and Livestock Research Organization (KALRO) advocates for soil health, a full lab analysis for Nitrogen (N), Phosphorus (P), Potassium (K), and pH can be expensive. Farmers often have to choose which specific soil metric to prioritize based on their limited budgets. Since different crops—ranging from the maize of the Rift Valley to the coffee of Central Kenya—thrive in vastly different chemical environments, planting the wrong crop in the wrong soil leads to wasted seasons and financial loss.

The Goal: As a Machine Learning collaborator, the objective is to determine which single soil nutrient is the most reliable predictor for crop suitability. By identifying the "most impactful" feature, we can help farmers prioritize their soil testing budget effectively.

📊 The Dataset: soil_measures.csv
The dataset represents various soil samples across diverse Kenyan-like agro-ecological zones.

N: Nitrogen content ratio (essential for leaf growth).

P: Phosphorous content ratio (vital for root development and energy transfer).

K: Potassium content ratio (critical for disease resistance and water regulation).

pH: The acidity or alkalinity of the soil (affects nutrient availability).

crop: The optimal crop for those specific conditions (e.g., maize, coffee, jute, rice, etc.).

🛠 Implementation & Solution
To solve this, we implemented a Multi-Class Classification workflow. Because the target variable (crop) contains 22 distinct categories, we utilized a Multinomial Logistic Regression approach.

1. Data Preprocessing
Checked for missing values to ensure data integrity.

Verified the nature of the target variable (22 unique crop types).

Split the data into Training (75%) and Testing (25%) sets, using stratification to ensure that rare crops were represented equally in both sets.

2. Feature Evaluation Strategy
Rather than building one complex model, we built four individual models—one for each soil metric. This allowed us to isolate the predictive power of Nitrogen, Phosphorus, Potassium, and pH independently.

3. Performance Metric
We used the Weighted F1-Score to evaluate the models. This metric is superior to simple accuracy for this problem because it balances Precision and Recall, accounting for any imbalance in the number of samples for different crops.

🚀 Key Results
The project outputs a dictionary containing the F1-scores for each metric:

Nitrogen (N)

Phosphorous (P)

Potassium (K)

pH

The final output is the best_predictive_feature, identifying the single most important metric a farmer should test for if they can only afford one.

📂 How to Run
Ensure you have pandas, numpy, and scikit-learn installed.

Place soil_measures.csv in the root directory.

Run the analysis script to generate the feature_performance dictionary.

Author: wickliff momanyi aspiring analytical engineer

Focus: Precision Agriculture for Kenyan Smallholder Farmers
