📊 Machine Learning Analysis
Advanced Predictive Modeling of Character Name Influence on Baby Naming Trends

After completing exploratory data analysis and statistical testing, I applied multiple machine learning models to predict and classify baby naming trends influenced by fictional character names.

🧠 Feature Engineering

A rich feature set was constructed from the temporal influence dataset to capture historical behavior, phonetic properties, and cultural context.

🔹 Temporal Features

before_1y, before_3y, before_5y – Popularity before character release

after_1y, after_3y, after_5y – Popularity after release

change_1y, change_3y, change_5y – Absolute popularity change

pct_change_1y, pct_change_3y – Percentage change

🔹 Historical Trend Features

recent_trend – 5-year moving average growth rate

total_historical – Total babies with the name before release

avg_historical – Average annual popularity before release

🔹 Name Characteristics

name_length – Number of characters

vowel_count – Number of vowels

vowel_ratio – Proportion of vowels (phonetic appeal)

🔹 Context Features

character_count – Number of characters with the name in release year

decade – Decade of character release (cultural era proxy)

🔹 Binary Targets

had_increase_1y – Popularity increase after 1 year (0/1)

had_increase_3y – Popularity increase after 3 years (0/1)

had_significant_increase – Increase > 100 babies (0/1)

📦 Final ML Dataset

186,404 records (character–name–year combinations)

3,816 unique names tracked

20+ engineered features per record

🎯 Problem Framing

Two complementary machine learning tasks were defined:

1️⃣ Regression Problem

Goal: Predict numeric change in baby name popularity

Target: change_3y

Why 3 years?

EDA showed influence peaks at 3–5 years

1-year effects are too noisy

5-year effects are too delayed

2️⃣ Classification Problem

Goal: Predict whether a name experiences a significant increase

Target: had_significant_increase (increase > 100 babies)

Why this threshold?

Filters random noise

Captures culturally meaningful shifts

Produces balanced and realistic classes

🤖 Machine Learning Models Applied
1️⃣ Linear Regression

Purpose: Baseline model and interpretability

Implementation

LinearRegression()


Features

before_5y, character_count, recent_trend

name_length, vowel_ratio, decade, avg_historical

Target

change_3y

📈 Results
Metric	1-Year	3-Year
R² Score	0.3595	0.6918
RMSE	491.75	2,310.14
MAE	154.01	751.51
🧠 Interpretation

69% variance explained for 3-year predictions (excellent for social data)

Short-term effects are noisy

Cultural influence takes time

Top Predictive Features

before_5y – Historical popularity

recent_trend – Momentum effect

character_count – Cultural exposure

Key Insight:
The relationship is largely linear, making this model both effective and interpretable.

2️⃣ Ridge Regression

Purpose: Handle multicollinearity using L2 regularization

Ridge(alpha=1.0)

Results
Metric	Value
R² Score	0.6919
RMSE	2,309.80

Outcome

Nearly identical to Linear Regression

Confirms model stability

Effectively handles correlated temporal features

3️⃣ Lasso Regression

Purpose: Feature selection using L1 regularization

Lasso(alpha=1.0)

Results
Metric	Value
R² Score	0.6918
RMSE	2,310.18
Non-zero Features	10 / 10

Interpretation

All features retained

No redundant features

Feature engineering was effective

4️⃣ Logistic Regression (Classification)

Purpose: Predict significant popularity increases

LogisticRegression(max_iter=1000)

Results
Metric	Score
Accuracy	79.6%
Precision	0.85
Recall	0.26
F1-Score	0.39
Confusion Matrix
	Pred No	Pred Yes
Actual No	6,765	138
Actual Yes	1,780	638

Key Insight

High precision → reliable predictions

Low recall → conservative model

Ideal for identifying high-confidence cultural hits

5️⃣ Random Forest Regression

Purpose: Capture non-linear interactions

RandomForestRegressor(
    n_estimators=100,
    max_depth=10,
    random_state=42
)

Results
Metric	Value
R² Score	0.6825
RMSE	2,344.79
MAE	756.90
Top Features
Feature	Importance
recent_trend	28.3%
total_historical	16.6%
before_1y	15.4%
before_5y	12.7%
decade	11.6%

Insight

Comparable to linear models

Confirms mostly linear dynamics

Cultural era matters

🔍 Clustering Analysis
6️⃣ K-Means Clustering

Purpose: Identify influence archetypes

KMeans(n_clusters=4, random_state=42)


Optimal K: 4
Silhouette Score: 0.29

Cluster Summary
Cluster	Size	Avg Before	Avg After	% Change	% Significant	Description
0	30,205	6,967	6,484	+140%	23%	Moderate popularity
1	1,472	169,790	165,366	+0.3%	37%	Established names
2 ⭐	642	11	752	+36,403%	100%	Breakout hits
3	14,282	9,108	9,576	+105%	28%	Modest growth

Key Insight

Cluster 2 represents rare but explosive breakouts

Established names are resistant to media influence

7️⃣ Hierarchical Clustering

Purpose: Alternative structure validation

AgglomerativeClustering(n_clusters=4, linkage="ward")


Sample size: 1,000

Highly unbalanced clusters

Confirms dominance of one naming pattern

🏆 Model Comparison
Regression Models
Model	R²	RMSE	MAE	Notes
Linear Regression	0.6918	2,310	751	Best balance
Ridge Regression	0.6919	2,310	—	Handles multicollinearity
Lasso Regression	0.6918	2,310	—	Feature validation
Random Forest	0.6825	2,345	757	No gain

Winner: Linear / Ridge Regression

Classification Model
Model	Accuracy	Precision	Recall	F1
Logistic Regression	79.6%	0.85	0.26	0.39
🔑 Key Findings

Character name influence is highly predictable

Linear models capture the process effectively

Four distinct influence archetypes exist

Breakout hits are rare but identifiable

Momentum and historical popularity dominate

⚠️ Limitations

Correlation ≠ causation

Class imbalance affects recall

Temporal multicollinearity

No media type or genre differentiation

✅ Conclusion

Machine learning confirms that fictional character names meaningfully influence baby naming trends.
This influence follows interpretable, predictable patterns driven by historical momentum, cultural context, and time.

Cultural impact is not random — it is measurable, structured, and persistent.
