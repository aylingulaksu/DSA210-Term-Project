# Exploring the Influence of Fictional Character Names on Popular Baby Names in the US ✧🎥🎞️˚

## Idea of Project
In this project, my aim is to analyze the relationship between **fictional character names** and **real-world baby name trends** in the US over time. My goal is to explore whether names of characters from movies influence the popularity of baby names and how closely fictional trends align with real-life naming patterns.

## Description of Dataset

### Baby Names Dataset
- **Source:** [US Baby Names by Year of Birth](https://www.kaggle.com/datasets/thedevastator/us-baby-names-by-year-of-birth)  
- **Content:** Includes name, gender, count, and year of birth for babies registered in the US.  
- **Purpose:** To analyze the yearly popularity of real-world names and detect trends.

### Character Names Dataset
- **Source:** [CMU Movie Dataset](https://www.cs.cmu.edu/~ark/personas/)  
- **Content:** Contains fictional character names along with associated personas, story context, and media type.  
- **Purpose:** To extract character names from media and analyze their popularity and overlap with real baby names.

## Plan

### Data Collection
- Download the baby names dataset from Kaggle.  
- Parse or scrape the CMU Movie dataset to extract character names.  
- Collect additional metadata for characters if available, such as media type, release year, and genre.

### Data Preparation and Analysis
- Normalize names in both datasets to account for capitalization and spelling differences.  
- Aggregate baby names by year to determine annual popularity rankings.  
- Aggregate character names by release year or media year if available.  
- Merge datasets to compare overlaps, trends, and unique patterns.  
- Perform exploratory data analysis (EDA) to visualize trends, peaks, and overlaps.

## Constructing Hypotheses
- **Null Hypothesis (H0):** Fictional character names have no significant effect on the popularity of real-world baby names.  
- **Alternative Hypothesis (H1):** Fictional character names significantly influence the popularity of real-world baby names.

## Machine Learning Models and Analysis
- **Trend Analysis:** Use correlation metrics to identify relationships between character name popularity and baby name trends.  
- **Time-Series Analysis & Regression:**  
  - Apply **linear regression** to model the relationship between fictional character popularity and real-world baby name counts over time.  
  - Use features such as media mentions per year, type of media, and release year to predict baby name popularity.  
  - Consider **lag variables** to account for delayed influence of fictional characters on baby naming trends.  
- **Clustering:** Group names to detect patterns where fictional influence might be stronger in certain decades or media types.   
- **Clustering:** Group names to detect patterns where fictional influence might be stronger in certain decades or media types.  

## Expected Outcomes
- Insights into how fictional media influences real-world naming trends.  
- Visualizations comparing popularity trajectories of real and fictional names.  
- Identification of names that cross over from fiction into real-life popularity.  
- Understanding of temporal patterns in naming and media influence.

## Tools & Technologies
- Python (pandas, numpy, matplotlib, seaborn, plotly)  
- Web scraping (BeautifulSoup or requests for character name extraction)  
- Jupyter Notebook for analysis  
