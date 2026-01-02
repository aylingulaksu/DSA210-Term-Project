# 🎥🎞️ Fictional Characters & Baby Names: A 130-Year Data Science Exploration
### *Analyzing the Influence of Media on Real-World Naming Trends in the US (1880–2016)*

##  Project Overview
Does a blockbuster movie or a hit TV show change what a generation names its children? This project explores the intersection of **pop culture and sociology** using Data Science. By merging US Social Security baby name records with the CMU Movie Summary Corpus, I analyzed whether character appearances lead to measurable surges in naming popularity.

---

##  The Datasets

###  US Baby Names (Social Security Administration)
- **Source:** Kaggle (US Baby Names by Year of Birth)
- **Scope:** 1880–2015
- **Scale:** 312M+ total babies across 6,917 unique names.
- **Processing:** Normalized name casing and stripped whitespace for matching.

###  CMU Movie Character Metadata
- **Source:** Carnegie Mellon University Movie Summary Corpus
- **Scope:** 1895–2016
- **Scale:** 147,477 valid character records.
- **Processing:** Since parents primarily use first names, I split compound names (e.g., "Rachel Green" ➔ "Rachel") to capture true naming influence.

---

##  Exploratory Data Analysis (EDA) & Statistical Findings

###  The "Lag Effect"
Statistical testing revealed that name influence is **not immediate**. There is a measurable delay between a character's release and its peak impact on birth certificates.

| Time After Release | Average % Change |
|-------------------|------------------|
| **1 Year Later** | **−20.2%** (No significant spike) |
| **3 Years Later** | **+343.2%** (Significant Growth) |
| **5 Years Later** | **+990.2%** (Massive Influence) |

###  Hypothesis Testing
- **H₀ (Null):** Character names have no effect on baby naming trends.
- **H₁ (Alternative):** Character names significantly increase baby name popularity.

**Results:**
- **3-Year Window:** P-value < 0.000001 ( Reject H₀)
- **5-Year Window:** P-value < 0.000001 ( Reject H₀)
- **ANOVA Test:** Confirmed that the change in popularity across different time windows is statistically significant.

---

##  Machine Learning Analysis
I applied advanced predictive modeling to determine if these cultural shifts follow predictable rules or random noise.

###  Feature Engineering
To improve model accuracy, I engineered over **20 features**, including:
- **Phonetic Properties:** Vowel ratios and name lengths.
- **Historical Momentum:** 5-year moving average growth rates.
- **Contextual Data:** Character counts per release year and decade-based cultural markers.



###  Model Performance

#### 1. Regression Task: Predicting Numeric Count Change
I aimed to predict the absolute change in baby counts three years post-release.

| Model | R² Score | Strength |
| :--- | :--- | :--- |
| **Linear Regression** | **0.69** | High Interpretability |
| **Ridge Regression** | **0.69** | Handles Multicollinearity |
| **Random Forest** | 0.68 | Captures Non-linear bursts |

**Key Insight:** Linear dynamics dominate. A name's **historical momentum** combined with **character frequency** explains ~69% of the variance in naming surges.

#### 2. Classification Task: Predicting "Breakout Hits"
Targeting "Spikes" (defined as a surge of >100 babies).

- **Logistic Regression Accuracy:** 79.6%
- **Precision:** 0.85 (High reliability in predicting hits)
- **Recall:** 0.26 (Model is conservative; breakout hits are rare and hard to catch)

---

##  Influence Archetypes (Clustering)
Using **K-Means Clustering (K=4)**, I identified four distinct ways names react to media:

1.  **The Breakout Hits:** Low baseline popularity that explodes post-release (e.g., *Cadence*, *Gage*).
2.  **The Established Classics:** High-volume names (e.g., *James*) where a movie has minimal marginal impact.
3.  **The Moderate Risers:** Names that see a steady, non-explosive climb.
4.  **The Fading Trends:** Names where media exposure failed to stop a downward trend.



---

##  Top Influenced Name Case Studies
| Name | Release Year | Before Count | After (3y) | % Increase |
| :--- | :--- | :--- | :--- | :--- |
| **Jeffrey** | 1939 | 157 | 2,681 | **+1,597%** |
| **Cadence** | 2003 | 232 | 3,840 | **+1,548%** |
| **Gage** | 1990 | 171 | 2,231 | **+1,197%** |
| **Justice** | 1993 | 267 | 3,277 | **+1,123%** |



---

##  Key Takeaways
1. **Fiction Drives Reality:** Media exposure is a statistically significant driver of US naming trends.
2. **The 3-Year Rule:** Influence peaks 3 to 5 years after release, accounting for the time it takes for a character to enter the "cultural zeitgeist" and for parents to complete pregnancy cycles.
3. **Predictability:** Cultural impact is not random. Using historical momentum and character frequency, we can predict naming surges with high accuracy.
4. **Consistency:** This phenomenon is not new; it has remained a consistent part of American culture from the 1910s to the 2010s.

---

##  Limitations & Future Work
- **Causation vs. Correlation:** While the statistical link is strong, external cultural factors (celebrity news, fashion) may also play a role.
- **Genre Analysis:** Future versions could distinguish if "Villains" vs. "Heroes" or "Sci-Fi" vs. "Romance" have different strengths of influence.
- **Global Scope:** Expanding this to non-US datasets to see if media influence is a universal human behavior.

---
**Tools Used:** Python (Pandas, Scikit-Learn, Statsmodels), Matplotlib, Seaborn.
