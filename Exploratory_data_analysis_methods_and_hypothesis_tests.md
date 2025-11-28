# ✧🎥🎞️⋆˙ Do Fictional Characters Influence Baby Names?  
### *A Data-Driven Exploration of How Movies & TV Shape Real-World Naming Trends (1880–2016)*

## 📌 Project Overview
In this project, I analyzed whether **fictional character names** from movies and TV shows influence what people name their babies in the United States.  
Using **US baby name data (1880–2015)** and **movie character data (1895–2016)**, I examined whether character appearances correlate with measurable increases in baby name popularity over time.

---

# 📂 The Data

## 👶 Baby Names Dataset
- **Source:** Kaggle — US Baby Names by Year of Birth  
- **Size:** 224,261 records  
- **Years:** 1880–2015  
- **Fields:** name, gender, count, birth year  
- **Total babies:** 312M+  
- **Unique names:** 6,917  

### 🧹 Cleaning
- Removed trailing spaces  
- Capitalized names consistently  
- Removed records with missing names/years  

Dataset was clean and easy to work with.

---

## 🎭 Character Names Dataset
- **Source:** CMU Movie Summary Corpus  
- **Size:** 450,669 character records  
- **Years:** 1895–2016  
- **Fields:** character name, actor, gender, release date  
- **Valid characters:** 147,477  

### 🧹 Cleaning
- Converted release dates into `datetime` format  
- Removed characters without names or release years  
- Removed blank or empty names  

**Final cleaned dataset:** 147,477 valid characters.

---

# 🔑 Splitting Character Names
Movie characters often have multi-part names like:

- `"Rachel Green"` → `["Rachel", "Green"]`  
- `"Lieutenant Melanie Ballard"` → `["Lieutenant", "Melanie", "Ballard"]`

Parents normally choose **first names**, so splitting captures actual naming influence.

### 📊 Results of the Split
- Original character names: **147,477**  
- After splitting: **256,592 individual names**  
- Unique names: **54,335**  
- Average: **1.74 names per character**

---

# 📈 Creating the Analysis Dataset
For each *character name*, I measured baby name popularity:

- **Before release** → Total babies with that name  
- **After release** → Popularity 1, 2, 3, and 5 years later  
- Calculated **percentage change** to detect influence  

### 📊 Final Analysis Dataset
- **155,112** character-year combinations  
- **186,404** total comparisons  
- **3,816** unique names tracked  
- **1,471** names showed increases (**38.5%**)  

---

# 📉📈 What I Found

## ⭐ Main Pattern: The Effect Takes Time
| Time After Release | Average % Change |
|-------------------|------------------|
| **1 year later**  | **−20%** (decrease) |
| **3 years later** | **+343%** |
| **5 years later** | **+990%** |

**Interpretation:**  
Names do **not** spike immediately. The influence grows slowly as characters gain cultural traction.

Parents:  
- discover the character  
- see if it becomes popular  
- have a baby  
- choose the name  

This explains the 2–3 year delay.

---

# 🌟 Real Examples: Names That Exploded in Popularity

## **Jeffrey (1939)**  
Before: 157 babies  
3 years after: 2,681 babies  
**Increase: +1,597% 🚀**

| Year | Babies Named Jeffrey |
|------|----------------------|
| 1938 | 157 |
| 1939 | 378 |
| 1940 | 801 |
| 1941 | 1,502 |
| 1942 | 2,058 |
| 1943 | 2,171 |
| 1944 | 2,328 |

## **Cadence (2003)**  
- Before: 232  
- After: 3,840  
- **Increase: +1,548%**

## **Gage (1990)** — +1,197%  
## **Justice (1993)** — +1,123%  
## **Liz (1957)** — +1,116%  

---

# 📊 More Names That Became Popular

| Name | Year | Before | After | % Increase |
|------|------|--------|--------|-----------|
| Dawson | 1998 | 828 | 7,009 | +746% |
| Vanessa | 1953 | 872 | 7,343 | +741% |
| Bentley | 2008 | 596 | 4,880 | +718% |
| Peyton | 1990 | 107 | 832 | +671% |
| Declan | 1997 | 105 | 709 | +570% |

---

# 🧪 Statistical Testing

## 🎯 Hypotheses
- **H₀:** Character names have *no* effect on baby names  
- **H₁:** Character names *increase* baby name popularity  

---

## ✔️ Test 1 — T-Test  
### **1 Year After Release**
- Avg change: **−20.20%**  
- P-value: **0.999994**  
- ❌ No significant effect  

### **3 Years After Release**
- Avg change: **+343.18%**  
- Sample size: 46,601  
- P-value: **< 0.000001**  
- ✅ **Significant effect**

### **5 Years After Release**
- Avg change: **+990.24%**  
- P-value: **< 0.000001**  
- ✅ **Very significant effect**

---

## ✔️ Test 2 — ANOVA  
**Question:** Do different time windows matter?

- 1 year: −20%  
- 3 years: +343%  
- 5 years: +990%  
- ✔️ **Yes, the changes across time windows are significantly different**

---

## ✔️ Test 3 — Proportion Test  
Is >50% of names increasing?

- In 3–5 year windows: **significantly more than half increase**  
- Not random — clear influence

---

# 🧾 Conclusions

## ✅ 1. Fictional characters *do influence* baby names  
And the effect is **strong** and **statistically significant**.

## ✅ 2. The effect is delayed  
- Year 1 → slight decrease  
- Years 3–5 → huge increases  

## ✅ 3. The increases are massive  
Some names rise **over +1,000%**.

## ✅ 4. This has been happening for over a century  
Examples found from:
- 1910s (Billy, Elwood)  
- 1950s (Liz, Vanessa)  
- 1990s (Gage, Peyton)  
- 2000s (Cadence, Bentley)  

## ✅ 5. This phenomenon is widespread  
- Analyzed: 3,816 names  
- Increases: 1,471  
- Affects thousands of families  

---

# 🧩 Limitations
- Cannot prove **pure causation**  
- Possible missing movie/TV releases  
- Name-splitting may introduce false matches  
- Did not distinguish movies vs TV, genres, or cultural contexts  

---

# 🔮 Future Ideas
- Compare naming effects by:
  - genre  
  - movie success / box office  
  - TV vs movies  
  - region within the US  
- Predict which character names will become popular  
- Build a dashboard or ML model for forecasting  

---

# 📊 Visualizations Generated
- Distribution plots: % change at 1, 3, 5 years  
- Bar charts of average increases  
- Time-series plots of individual names  
- Case-study plots for top influenced names  

---

# 📚 References
- US Baby Names Dataset (Kaggle)  
- CMU Movie Summary Corpus  

---

# ⭐ Summary
**Fiction influences reality — massively.**  
Character names lead to huge, measurable increases in baby name popularity, especially 3–5 years after a character appears.  
This effect has existed for over **100 years** and continues today.

