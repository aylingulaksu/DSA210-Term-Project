✧🎥🎞️✮⋆˙
Exploring the Influence of Fictional Character Names on Popular Baby Names in the US
Idea of Project

In this project, I analyzed whether fictional character names from movies and TV shows have a measurable influence on baby naming trends in the United States. Using more than a century of data, the goal was to determine if character names become more popular after their on-screen appearance — and if so, how strong and how delayed this effect is.

📚 Description of the Datasets
Baby Names Dataset 👶🍼

Source: Kaggle – US Baby Names by Year of Birth

Years: 1880–2015

Size: 224,261 records (312M+ babies)

Unique Names: 6,917

Fields: name, gender, birth year, count

Cleaning Steps:

Standardized capitalization

Removed rows with missing names or years

Ensured consistent formatting

Purpose: Track year-by-year popularity of real baby names.

Character Names Dataset 🎭

Source: CMU Movie Summary Corpus

Years: 1895–2016

Size: 450,669 character entries

Valid Characters After Cleaning: 147,477

Fields: character name, actor, movie, release date

Cleaning Steps:

Converted release dates to proper datetime formats

Removed entries with missing names or years

Filtered out empty or placeholder names

Purpose: Extract fictional character names and map them to their release years.

🧹 Key Data Processing Step: Splitting Character Names

Character names often include multiple parts:

“Rachel Green”

“Lieutenant Melanie Ballard”

But parents usually pick only one of those parts when naming babies.

So each character name was split into individual components:

"Rachel Green" → ["Rachel", "Green"]

"Lieutenant Melanie Ballard" → ["Lieutenant", "Melanie", "Ballard"]

This helps detect real influences even if the baby name matches just one part.

Results of Splitting:

147,477 full names → 256,592 individual name tokens

54,335 unique individual names

Avg 1.74 tokens per character

🧪 Building the Analysis Dataset

For every character name (token) and its release year, I computed:

Popularity before the character appeared

Popularity 1, 2, 3, and 5 years later

Percentage increase or decrease

Final Analysis Dataset:

155,112 character name–year combinations

186,404 total comparisons

3,816 unique names tracked

1,471 names showed measurable increases (38.5%)

📈 Results
⏳ The Key Pattern: Influence Takes Time
Years After Release	Avg % Change
1 year	–20% (decrease)
3 years	+343%
5 years	+990%

Names do not immediately become popular after a character appears.
Instead, there's a 2–3 year delay, likely because:

people need time to watch the show/movie

character popularity must spread culturally

parents need to actually have a baby during that time

🌟 Real Examples of Names That Skyrocketed
Jeffrey (1939)

Before release: 157 babies
3 years later: 2,681 babies
➡️ +1597% increase

Year-by-year:

1938: 157

1939: 378 ← character released

1940: 801

1941: 1,502

1942: 2,058

1943: 2,171

1944: 2,328

Other Big Increases
Name	Year	Before	After	Increase
Cadence	2003	232	3,840	+1548%
Gage	1990	171	2,231	+1197%
Justice	1993	267	3,277	+1123%
Liz	1957	117	1,435	+1116%
Dawson	1998	828	7,009	+746%
Vanessa	1953	872	7,343	+741%
Bentley	2008	596	4,880	+718%
Peyton	1990	107	832	+671%
Declan	1997	105	709	+570%
🧪 Statistical Testing
Hypotheses

H₀: Character names have no effect on baby naming trends

H₁: Character names increase baby name popularity

1. T-Tests
1 Year After Release

Avg: –20.20%

p-value: 0.999994
❌ No significant effect

3 Years After Release

Avg: +343.18%

N = 46,601

p-value: < 0.000001
✅ Very significant

5 Years After Release

Avg: +990.24%

p-value: < 0.000001
✅ Extremely significant

2. ANOVA

Groups: 1-year vs 3-year vs 5-year changes
➡️ Large statistically significant difference
➡️ The influence increases the longer the time window.

3. Proportion Test

In the 3–5 year windows:
✔ Significantly more than half of character names lead to increases.

🧠 Conclusions
✔ Fictional characters do influence baby names

And the effect is massive, widespread, and statistically undeniable.

✔ The effect appears after 2–3 years

Immediate influence is rare — trends need time to grow.

✔ Some names see 1000%+ jumps

Fiction shapes real naming culture in measurable ways.

✔ This trend has existed for over 100 years

From the 1910s to the 2000s.

✔ Around 38.5% of all tracked names increase

Thousands of families follow naming inspiration from media.

⚠️ Limitations

Cannot prove absolute causation (correlation ≠ causation)

Some character releases may be missing or misdated

Splitting names may over-match in some cases

Did not differentiate movies vs TV, nor genres

Did not analyze gender-specific effects

🚀 Future Ideas

Compare impact by box office success

Study genre effects (romance vs fantasy vs horror)

Geographic breakdown within the US

Predictive modeling of future baby name trends

Compare film vs TV influences separately

📊 Visualizations Created

Distribution charts of % changes

Bar plots of average changes over time

Time-series plots for specific names

Case studies of the largest increases

📚 References

US Baby Names Dataset (Kaggle)

CMU Movie Summary Corpus
