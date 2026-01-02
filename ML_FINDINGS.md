✧🤖📊⋆˙ Machine Learning Analysis
Advanced Predictive Modeling of Character Name Influence on Baby Naming Trends

After completing exploratory data analysis and statistical testing, I applied multiple machine learning models to predict and classify baby naming trends influenced by fictional character names.

🧠✨ Feature Engineering

Before applying machine learning models, I created a rich feature set from the temporal influence dataset to capture historical behavior, phonetic properties, and cultural context.

⏳ Temporal Features

before_1y, before_3y, before_5y → Popularity before character release

after_1y, after_3y, after_5y → Popularity after release

change_1y, change_3y, change_5y → Absolute change in popularity

pct_change_1y, pct_change_3y → Percentage change

📜 Historical Trend Features

recent_trend → 5-year moving average growth rate

total_historical → Total babies with the name before release

avg_historical → Average annual popularity before release

🔤 Name Characteristics

name_length → Number of characters

vowel_count → Number of vowels

vowel_ratio → Proportion of vowels (phonetic appeal)

🎬 Context Features

character_count → Number of characters with the name in release year

decade → Decade of character release (captures cultural era)

🎯 Binary Targets

had_increase_1y → Increase 1 year after release (0/1)

had_increase_3y → Increase 3 years after release (0/1)

had_significant_increase → Increase >100 babies (0/1)

📦📊 Final Machine Learning Dataset

186,404 character–name–year records

3,816 unique names tracked over time

20+ engineered features per observation

🎯🧩 Problem Framing

I framed the analysis as two machine learning tasks.

1️⃣ Regression Task
Predicting numeric popularity change

Target variable: change_3y

Why 3 years?

EDA showed influence peaks around 3–5 years

1-year changes are too noisy

5-year effects are too delayed

2️⃣ Classification Task
Predicting significant popularity increases

Target variable: had_significant_increase

Threshold: increase >100 babies

Why this threshold?

Filters random noise

Captures culturally meaningful surges

Produces balanced, realistic classes

🤖📈 Machine Learning Models
1️⃣ Linear Regression
Baseline & interpretability

Purpose:
Establish a baseline model and understand linear relationships.

Key Results

Metric	1-Year	3-Year
R²	0.36	0.69
RMSE	491.75	2,310.14
MAE	154.01	751.51

Key Insight:
3-year predictions explain ~69% of variance, which is excellent for social and cultural data.

Top Predictive Features

before_5y → Historical popularity

recent_trend → Momentum effect

character_count → Cultural exposure

2️⃣ Ridge Regression
Handling multicollinearity

Regularization via L2 penalty

Stabilizes correlated temporal features

Metric	Value
R²	0.69
RMSE	2,309.80

Outcome:
Nearly identical to Linear Regression, confirming model stability.

3️⃣ Lasso Regression
Feature selection validation

L1 regularization

Tests redundancy in engineered features

Metric	Value
R²	0.69
Non-zero features	10 / 10

Insight:
All features contribute meaningfully → feature engineering was effective.

4️⃣ Logistic Regression
Predicting significant name surges
Metric	Score
Accuracy	79.6%
Precision	0.85
Recall	0.26
F1-score	0.39

Interpretation

High precision → reliable predictions

Low recall → conservative model

Ideal for identifying high-confidence cultural hits

5️⃣ Random Forest Regression
Non-linear modeling
Metric	Value
R²	0.68
RMSE	2,344.79
MAE	756.90

Top Features

recent_trend

total_historical

before_1y, before_5y

decade

Key Insight:
Non-linear models do not outperform linear ones → the process is largely linear.

🧩🔍 Clustering Analysis
6️⃣ K-Means Clustering
Identifying influence archetypes

Optimal clusters: K = 4

Silhouette score: 0.29

🌟 Cluster Highlights

⭐ Breakout Hits

Very low initial popularity

Explode after character release

100% experience significant increase

🏛️ Established Names

Already highly popular

Media exposure has minimal impact

📈 Moderate Growth Names

Some increase, not explosive

Key Insight:
Fictional influence follows four distinct behavioral patterns.

7️⃣ Hierarchical Clustering
Structural validation

Confirms dominance of one common pattern

Small clusters capture rare outliers

Less informative than K-Means for this dataset

🏆📊 Model Comparison
Regression Models
Model	R²	RMSE	Strength
Linear Regression	0.69	2,310	Interpretable
Ridge Regression	0.69	2,310	Stable
Lasso Regression	0.69	2,310	Feature validation
Random Forest	0.68	2,345	Non-linear

Winner: Linear / Ridge Regression

Classification Model
Model	Accuracy	Precision	Recall
Logistic Regression	79.6%	0.85	0.26
🔑✨ Key Takeaways

Character name influence is highly predictable

Linear dynamics dominate cultural naming trends

Momentum and history matter most

Breakout hits are rare but identifiable

Cultural impact follows measurable patterns

⚠️🧩 Limitations

Correlation ≠ causation

Class imbalance limits recall

Overlapping temporal features

Media types and genres not distinguished

🏁🌟 Conclusion

Fictional characters do influence baby names — and the effect is structured, delayed, and predictable.
Machine learning reveals that cultural trends follow interpretable rules, not randomness.
