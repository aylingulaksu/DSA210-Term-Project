# Exploring the Influence of Fictional Character Names on Popular Baby Names in the US

## Idea of Project
In this project, my aim is to analyze the relationship between **fictional character names** and **real-world baby name trends** in the US over time. My goal is to explore whether names of characters from literature, movies, games, and other media influence the popularity of baby names and how closely fictional trends align with real-life naming patterns.

## Description of Dataset

### Baby Names Dataset
- **Source:** [US Baby Names by Year of Birth](https://www.kaggle.com/datasets/thedevastator/us-baby-names-by-year-of-birth)  
- **Content:** Includes name, gender, count, and year of birth for babies registered in the US.  
- **Purpose:** To analyze the yearly popularity of real-world names and detect trends.

### Character Names Dataset
- **Source:** [CMU Personas Dataset](https://www.cs.cmu.edu/~ark/personas/)  
- **Content:** Contains fictional character names along with associated personas, story context, and media type.  
- **Purpose:** To extract character names from media and analyze their popularity and overlap with real baby names.

## Plan

### Data Collection
- Download the baby names dataset from Kaggle.  
- Parse or scrape the CMU Personas dataset to extract character names.  
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

**Additional hypotheses may include:**  
- Character names from widely popular media (movies, TV, games) influence baby names more than literary or niche media.  
- Male and female character names influence real-world naming trends differently.  
- Overlaps between fictional and real names vary over decades, reflecting cultural or media trends.

## Machine Learning Models and Analysis
- **Trend Analysis:** Use correlation metrics to identify relationships between character name popularity and baby name trends.  
- **Time-Series Analysis:** Apply regression models to predict shifts in baby name popularity based on fictional character influence.  
- **Clustering:** Group names to detect patterns where fictional influence might be stronger in certain decades or media types.  
- **Predictive Modeling (Optional):** Using features such as media type, character popularity, and release year, predict the likelihood that a fictional name becomes a popular baby name.

## Expected Outcomes
- Insights into how fictional media influences real-world naming trends.  
- Visualizations comparing popularity trajectories of real and fictional names.  
- Identification of names that cross over from fiction into real-life popularity.  
- Understanding of temporal patterns in naming and media influence.

## Tools & Technologies
- Python (pandas, numpy, matplotlib, seaborn, plotly)  
- Web scraping (BeautifulSoup or requests for character name extraction)  
- Jupyter Notebook for analysis  
- Optional: Dash or Streamlit for interactive dashboards
