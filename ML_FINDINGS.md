## ✧🤖📊⋆˙ Machine Learning Analysis
### Advanced Predictive Modeling of Character Name Influence on Baby Naming Trends

After completing exploratory data analysis and statistical testing, I applied multiple machine learning models to predict and classify baby naming trends influenced by fictional character names. 

---

## 🧠✨ Feature Engineering
Before applying machine learning models, I created a rich feature set from the temporal influence dataset to capture historical behavior, phonetic properties, and cultural context.

### ⏳ Temporal Features
* **before_1y, before_3y, before_5y:** Popularity before character release.
* **after_1y, after_3y, after_5y:** Popularity after release.
* **change_1y, change_3y, change_5y:** Absolute change in popularity.
* **pct_change_1y, pct_change_3y:** Percentage change.

### 📜 Historical Trend Features
* **recent_trend:** 5-year moving average growth rate.
* **total_historical:** Total babies with the name before release.
* **avg_historical:** Average annual popularity before release.

### 🔤 Name Characteristics
* **name_length:** Number of characters.
* **vowel_count:** Number of vowels.
* **vowel_ratio:** Proportion of vowels (phonetic appeal).

### 🎬 Context Features
* **character_count:** Number of characters with the name in release year.
* **decade:** Decade of character release (captures cultural era).

### 🎯 Binary Targets
* **had_increase_1y:** Increase 1 year after release (0/1).
* **had_increase_3y:** Increase 3 years after release (0/1).
* **had_significant_increase:** Increase >100 babies (0/1).

---

## 📦📊 Final Machine Learning Dataset
* **186,404** character–name–year records.
* **3,816** unique names tracked over time.
* **20+** engineered features per observation.

---

## 🎯🧩 Problem Framing
I framed the analysis as two distinct machine learning tasks:

### 1. Regression Task
**Predicting numeric popularity change.**
* **Target variable:** `change_3y`
* **Logic:** EDA showed influence peaks around 3–5 years. 1-year changes are too noisy, while 5-year effects are too delayed.

### 2. Classification Task
**Predicting significant popularity increases.**
* **Target variable:** `had_significant_increase`
* **Threshold:** Increase >100 babies.
* **Logic:** This filters out random noise and captures culturally meaningful surges, producing balanced, realistic classes.

---

## 🤖📈 Machine Learning Models

### 1️⃣ Linear Regression: Baseline & Interpretability
Establish a baseline model and understand linear relationships.

| Metric | 1-Year | 3-Year |
| :--- | :--- | :--- |
| **R²** | 0.36 | **0.69** |
| **RMSE** | 491.75 | 2,310.14 |
| **MAE** | 154.01 | 751.51 |

* **Key Insight:** 3-year predictions explain **~69% of variance**, which is excellent for social and cultural data.
* **Top Predictive Features:** `before_5y` (History), `recent_trend` (Momentum), `character_count` (Exposure).

### 2️⃣ Ridge Regression: Handling Multicollinearity
* **Regularization via L2 penalty** to stabilize correlated temporal features.
* **Result:** R² of **0.69**. Identical to Linear Regression, confirming model stability.

### 3️⃣ Lasso Regression: Feature Selection Validation
* **L1 regularization** to test redundancy.
* **Result:** **10/10 non-zero features**. All engineered features contribute meaningfully.

### 4️⃣ Logistic Regression: Predicting Name Surges
| Metric | Score |
| :--- | :--- |
| **Accuracy** | **79.6%** |
| **Precision** | 0.85 |
| **Recall** | 0.26 |
| **F1-score** | 0.39 |

High precision indicates reliable predictions, though a lower recall suggests the model is conservative—ideal for identifying high-confidence cultural hits.

### 5️⃣ Random Forest Regression: Non-linear Modeling
* **Metric (R²):** 0.68
* **Top Features:** `recent_trend`, `total_historical`, `decade`.
* **Insight:** Non-linear models did not significantly outperform linear ones, suggesting the underlying process is largely linear.

---

## 🧩🔍 Clustering Analysis

### 6️⃣ K-Means Clustering: Influence Archetypes
* **Optimal Clusters:** K = 4
* **Silhouette Score:** 0.29

**🌟 Cluster Highlights:**
* ⭐ **Breakout Hits:** Very low initial popularity; explode after character release.
* 🏛️ **Established Names:** Already highly popular; media exposure has minimal impact.
* 📈 **Moderate Growth Names:** Steady increase, not explosive.

### 7️⃣ Hierarchical Clustering
* **Result:** Confirmed the dominance of one common pattern and identified small clusters of rare outliers.

---

## 🏆📊 Model Comparison

### Regression Models
| Model | R² | RMSE | Strength |
| :--- | :--- | :--- | :--- |
| **Linear Regression** | 0.69 | 2,310 | Interpretable |
| **Ridge Regression** | 0.69 | 2,310 | Stable |
| **Random Forest** | 0.68 | 2,345 | Non-linear |

**Best Resulting Model:** Linear / Ridge Regression.

### Classification Model
| Model | Accuracy | Precision | Recall |
| :--- | :--- | :--- | :--- |
| **Logistic Regression** | 79.6% | 0.85 | 0.26 |

---

## 🔑✨ Key Takeaways
* **Predictability:** Character name influence is highly structured and predictable.
* **Linearity:** Linear dynamics dominate cultural naming trends.
* **Lag Effect:** Momentum and historical context matter more than the immediate release.
* **Rarity:** Breakout hits are rare but follow identifiable patterns.

---

## 🏁🌟 Conclusion
Fictional characters **do** influence baby names—and the effect is structured, delayed, and predictable. Machine learning reveals that cultural trends follow interpretable rules, not randomness.
