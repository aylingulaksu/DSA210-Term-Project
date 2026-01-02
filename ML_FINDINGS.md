Machine Learning Analysis
Advanced Predictive Modeling of Character Name Influence on Baby Naming Trends
After conducting exploratory data analysis and statistical testing, I applied various machine learning models to predict and classify naming trends influenced by fictional characters.

Feature Engineering
Before applying ML models, I created a rich feature set from the temporal influence dataset:
Features Created
Temporal Features:

before_1y, before_3y, before_5y → Popularity in years before character release
after_1y, after_3y, after_5y → Popularity in years after release
change_1y, change_3y, change_5y → Absolute change in popularity
pct_change_1y, pct_change_3y → Percentage change

Historical Trend Features:

recent_trend → Recent momentum (5-year moving average growth rate)
total_historical → Total babies with the name before release
avg_historical → Average annual popularity before release

Name Characteristics:

name_length → Number of characters in the name
vowel_count → Number of vowels
vowel_ratio → Proportion of vowels (phonetic appeal)

Context Features:

character_count → How many characters had this name in the release year
decade → Decade of character release (captures cultural eras)

Binary Targets:

had_increase_1y → Did popularity increase 1 year after? (0/1)
had_increase_3y → Did popularity increase 3 years after? (0/1)
had_significant_increase → Did popularity increase by >100 babies? (0/1)

Final ML Dataset

186,404 records (character-name-year combinations)
3,816 unique names tracked over time
20+ features for each record

Problem Framing
I approached this as two ML problems:
1️) Regression Problem
Goal: Predict the numeric change in baby name popularity after a character release
Target Variable: change_3y (change in popularity 3 years after release)
I decide on choosing 3 years because; based on EDA findings, the effect peaks around 3–5 years, balances immediate vs. long-term effects and it is more predictable than 1-year (too volatile) or 5-year (too delayed).

2️) Classification Problem
Goal: Predict whether a name will experience a significant increase (binary)
Target Variable: had_significant_increase (1 if increase >100 babies, 0 otherwise)
I chose this threshold beacuse it filters noise from random fluctuations, identifies culturally meaningful impacts, creates balanced classes for classification.


Machine Learning Models Applied
1. Linear Regression 
Purpose: Establish a baseline and understand linear relationships
Implementation:
pythonLinearRegression()
- Features: before_5y, character_count, recent_trend, name_length, 
           vowel_ratio, decade, avg_historical
- Target: change_3y (numeric popularity change)
Results:
Metric1-Year Prediction3-Year PredictionR² Score0.35950.6918RMSE491.752,310.14MAE154.01751.51
Interpretation:

✅ 69% of variance explained in 3-year predictions — excellent for social science data
1-year predictions are weaker (R² = 0.36) → immediate effects are noisy
3-year predictions are much more reliable → cultural influence takes time

Top 3 Predictive Features:

before_5y (coefficient: varies with correlation structure)

Historical popularity is the strongest predictor
Names already somewhat known are more likely to surge


recent_trend

Names gaining momentum continue to rise


character_count

More characters with the name → stronger cultural presence



Key Insight: The relationship between features and popularity change is largely linear, making this model interpretable and effective.

2. Ridge Regression 
Purpose: Handle multicollinearity and prevent overfitting through L2 regularization
Implementation:
pythonRidge(alpha=1.0)
- Same features as Linear Regression
- Adds penalty for large coefficients
Results:
MetricValueR² Score0.6919RMSE2,309.80
I used ridge because some features (before_1y, before_3y, before_5y) are highly correlated (overlap in time periods), ridge shrinks correlated coefficients toward each other, prevents model from being overly sensitive to multicollinearity.

Outcome: Nearly identical performance to Linear Regression → suggests the model is already well-regularized and stable.

3. Lasso Regression 
Purpose: Feature selection through L1 regularization (forces some coefficients to exactly zero)
Implementation:
pythonLasso(alpha=1.0)
- Same features as Linear Regression
- Adds penalty that can eliminate features
Results:
MetricValueR² Score0.6918RMSE2,310.18Non-zero features10/10
Interpretation:

All features retained → every feature adds predictive value
No redundant features in the model
Confirms feature engineering was effective


4. Logistic Regression 
Purpose: Binary classification — predict whether a name will have a significant increase
Implementation:
pythonLogisticRegression(max_iter=1000)
- Features: Same as regression models
- Target: had_significant_increase (0 or 1)
- Stratified train-test split
Results:
MetricScoreAccuracy79.57%Precision (Significant Increase)0.85Recall (Significant Increase)0.26F1-Score0.39
Confusion Matrix:
Predicted: NoPredicted: YesActual: No6,765138Actual: Yes1,780638
Interpretation:

High precision (85%) → When model predicts a big increase, it's usually correct
Low recall (26%) → Model misses many actual increases (conservative)
This is expected behavior — significant increases are rare events (~26% of cases)
Trade-off reflects real-world scenario: better to be cautious than oversell predictions

Key Insight: The model is a conservative predictor — it identifies high-confidence cases but doesn't catch every surge. Useful for identifying "safe bets" for cultural influence.

5. Random Forest Regression 
Purpose: Capture non-linear relationships and interactions between features
Implementation:
pythonRandomForestRegressor(n_estimators=100, max_depth=10, random_state=42)
- Ensemble of 100 decision trees
- Captures complex patterns
- Feature importance via Gini impurity
Results:
MetricValueR² Score0.6825RMSE2,344.79MAE756.90
Top 5 Features by Importance:
FeatureImportance Scorerecent_trend28.3%total_historical16.6%before_1y15.4%before_5y12.7%decade11.6%
Interpretation:

Performance comparable to Linear Regression → relationship is fairly linear
recent_trend is most important → names gaining momentum continue to rise
decade ranks high → cultural era matters (1950s names behave differently than 2000s names)

Key Insight: Non-linear methods don't dramatically outperform linear models, suggesting the underlying process follows linear dynamics with some noise.

Clustering Analysis
6. K-Means Clustering 
Purpose: Group names by similar influence patterns
Implementation:
pythonKMeans(n_clusters=4, random_state=42)
- Features: before_5y, after_5y, pct_change_3y, name_length, 
           character_count, decade
- Standardized features before clustering
- Used Elbow Method + Silhouette Score for optimal K
Optimal Clusters: K = 4
Silhouette Score: 0.2914 (moderate cohesion)
Cluster Characteristics:
ClusterSizeAvg BeforeAvg AfterAvg % Change% w/ Significant IncreaseDescription030,2056,9676,484+140%23%Moderate Popularity, Slight Increase11,472169,790165,366+0.3%37%Highly Popular, Stable ("Established Names")264211752+36,403%100%Breakout Hits ⭐314,2829,1089,576+105%28%Popular, Modest Growth
Interpretation:
Cluster 2 is the gold mine:

Very low initial popularity (11 babies)
Explodes to 752 babies after character release
Every single name in this cluster experienced significant increase
These are the "Cadence," "Gage," "Bentley" style breakouts

Cluster 1: Established names

Already mega-popular (169K babies)
Character appearances don't move the needle much
Examples: "James," "Michael," "Sarah"

Clusters 0 & 3: Middle ground

Moderate popularity
Some increase, but not explosive
Represents most names in the dataset

Key Insight: Clustering reveals four distinct influence archetypes, with rare but powerful "breakout hit" pattern for obscure names.

7. Hierarchical Clustering 
Purpose: Explore hierarchical relationships and alternative grouping structure
Implementation:
pythonAgglomerativeClustering(n_clusters=4, linkage='ward')
- Ward linkage minimizes within-cluster variance
- Visualized with dendrogram
- Sampled 1,000 records for computational efficiency
Results:
ClusterSize (of 1,000)Percentage071071.0%1303.0%224924.9%3111.1%
Interpretation:

Extremely unbalanced clusters → most names fall into one dominant pattern
Small clusters (1 and 3) represent rare outliers
Less informative than K-Means for this dataset

Key Insight: Hierarchical clustering confirms most names follow similar patterns, with a small subset behaving very differently (likely the "breakout hits").

Model Comparison & Evaluation
Regression Models (Predicting 3-Year Popularity Change)
ModelR² ScoreRMSEMAEProsConsLinear Regression0.69182,310751Interpretable, fastAssumes linearityRidge Regression0.69192,310—Handles multicollinearitySlightly less interpretableLasso Regression0.69182,310—Feature selectionDidn't eliminate any featuresRandom Forest0.68252,345757Captures non-linearityBlack box, no better performance
Winner: Linear Regression / Ridge

Simplest model with best performance
High interpretability
Coefficients reveal causal story


Classification Model (Predicting Significant Increases)
ModelAccuracyPrecisionRecallF1-ScoreLogistic Regression79.6%0.850.260.39
Interpretation:

High accuracy but imbalanced classes
Excellent for identifying "sure bets" (high precision)
Misses many actual increases (low recall) — acceptable trade-off


Key Findings from ML Analysis
1) Character Names Are Highly Predictable

69% of variance in popularity changes can be explained by historical data
Historical popularity + recent trends are strongest predictors

2️) Linear Relationships Dominate

Complex models (Random Forest) don't outperform Linear Regression
The underlying process follows interpretable, linear dynamics

3️) Four Distinct Influence Patterns Exist

Cluster analysis reveals clear archetypes
"Breakout hits" are rare but 100% predictable when they occur

4️) Significant Increases Are Rare But Identifiable

Only ~26% of names experience major surges
Logistic regression identifies these with 85% precision

5️) Best Predictors of Influence:

Recent naming trend (momentum effect)
Historical popularity (recognition factor)
Time window (3–5 years optimal)
Cultural era (decade) (context matters)

Limitations

Correlation ≠ Causation

Models predict patterns but don't prove character caused the change
Other factors (celebrities, events) could contribute


Class Imbalance

Most names don't change significantly
Makes predicting rare "breakout hits" challenging (low recall)


Multicollinearity in Temporal Features

Overlapping time windows (before_1y, before_3y) correlate
Addressed with Ridge regression and feature selection


No Genre/Media Type Differentiation

Blockbuster movies vs. indie films treated equally
TV shows vs. movies not distinguished



Conclusion
Machine learning analysis confirms and extends the findings from exploratory data analysis:
Character names DO influence baby names — and this influence is highly predictable
The effect follows clear patterns — captured by linear models with 69% accuracy
Four distinct influence archetypes exist — from "breakout hits" to "stable classics"
Historical popularity is destiny — names with momentum continue to rise
The models successfully predict naming trends, revealing that cultural influence is not random — it follows measurable, interpretable patterns that have persisted for over a century.
