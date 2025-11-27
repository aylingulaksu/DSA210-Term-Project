Do Fictional Characters Influence Baby Names?
Project Overview
In this project, I analyzed whether character names from movies and TV shows actually influence what people name their babies. I used US baby name data from 1880-2015 and movie character data from 1895-2016 to see if there's a real connection.

The Data
Baby Names Dataset
Source: Kaggle - US Baby Names by Year of Birth
Size: 224,261 records
Years: 1880-2015
Info: Name, birth year, gender, count
Total babies: 312 million+
Unique names: 6,917
Character Names Dataset
Source: CMU Movie Dataset
Size: 450,669 character records
Years: 1895-2016
Info: Character name, release date, actor, gender
Valid characters: 147,477
Data Cleaning
Cleaning the Baby Names
Removed spaces and capitalized names consistently
Removed any records with missing names or years
Pretty straightforward dataset to work with
Cleaning the Character Names
Converted release dates to proper datetime format
Removed characters without names or release years
Got rid of empty/blank character names
Final dataset: 147,477 characters from 1895-2016
The Big Idea: Splitting Character Names
This was the most important preprocessing step. Here's why:

Character names in movies are often like "Rachel Green" or "Lieutenant Melanie Ballard". But when parents name their babies, they usually just use one part - like "Rachel" or "Melanie".

So I split every character name into individual parts:

"Rachel Green" → ["Rachel", "Green"]
"Lieutenant Melanie Ballard" → ["Lieutenant", "Melanie", "Ballard"]
This way, if someone named their baby "Rachel" after Rachel Green, I'd catch it!

Results:

Started with 147,477 full character names
Split into 256,592 individual names
Found 54,335 unique individual names
Average of 1.74 names per character
Creating the Analysis Dataset
For each character name, I looked at baby name popularity:

Before the character appeared: How many babies had that name before the movie/show came out?
After the character appeared: How many babies had that name 1, 2, 3, and 5 years later?
Then I calculated the percentage change to see if there was an increase.

Final dataset:

155,112 unique character name-year combinations
186,404 total comparisons (across different time windows)
3,816 unique names tracked over time
1,471 names showed some increase (38.5%)
What I Found
The Main Pattern: It Takes Time!
Time After Character Release	Average % Change
1 year later	-20% (actually decreased!)
3 years later	+343% (more than 3x increase!)
5 years later	+990% (almost 10x increase!)
This was surprising! Names don't immediately jump in popularity. There's actually a delay of 2-3 years before you see the big increases. Makes sense though - parents need time to discover the character, see if it becomes popular, and then have a baby.

Real Examples: Names That Blew Up
Here are some names that got WAY more popular after a character appeared:

Jeffrey (1939)
Before the character: 157 babies
3 years after: 2,681 babies
Increase: 1,597% 🚀

Year by year:

1938: 157 babies
1939: 378 babies ← character released
1940: 801 babies
1941: 1,502 babies
1942: 2,058 babies
1943: 2,171 babies
1944: 2,328 babies
Cadence (2003)
Before: 232 babies
After: 3,840 babies
Increase: 1,548%

Gage (1990)
Before: 171 babies
After: 2,231 babies
Increase: 1,197%

Justice (1993)
Before: 267 babies
After: 3,277 babies
Increase: 1,123%

Liz (1957)
Before: 117 babies
After: 1,435 babies
Increase: 1,116%

More Names That Got Popular
Name	Year	Before	After	% Increase
Dawson	1998	828	7,009	+746%
Vanessa	1953	872	7,343	+741%
Bentley	2008	596	4,880	+718%
Peyton	1990	107	832	+671%
Declan	1997	105	709	+570%
Statistical Testing
I needed to prove these patterns weren't just coincidence, so I ran some statistical tests.

My Hypotheses
Null Hypothesis (H₀): Character names have NO effect on baby names
Alternative Hypothesis (H₁): Character names DO increase baby name popularity
Test 1: T-Test (Are the averages really different from zero?)
1 Year After Release:

Average change: -20.20%
P-value: 0.999994
Result: No significant effect ❌
Makes sense - too early!
3 Years After Release:

Average change: +343.18%
Sample size: 46,601
P-value: < 0.000001
Result: SIGNIFICANT EFFECT! ✅
This is strong evidence that character names matter!
5 Years After Release:

Average change: +990.24%
P-value: < 0.000001
Result: VERY SIGNIFICANT EFFECT! ✅✅
The effect gets even stronger over time!
Test 2: ANOVA (Does the effect change over time?)
I tested whether the influence is different at 1 year vs 3 years vs 5 years.

Group Averages:

1 year: -20%
3 years: +343%
5 years: +990%
Result: Yes, the time window matters A LOT! The influence gets progressively stronger over time.

Test 3: Proportion Test (Do more than half of names increase?)
I checked if more than 50% of names increase after a character appears.

Result: In the 3-5 year windows, significantly more than half of character names lead to baby name increases. This isn't random - it's a real pattern.

Conclusions
What I Learned
1. Yes, fictional characters DO influence baby names!

The evidence is really strong:

3 years after a character appears: average +343% increase
5 years after: average +990% increase
P-values < 0.000001 (basically impossible to happen by chance)
2. It takes time for the effect to happen

Year 1: Actually a slight decrease (-20%)
Years 3-5: Huge increases (+343% to +990%)
This delay makes sense - parents need time to:

Watch the movie/show
See if the character becomes culturally significant
Decide they like the name
Have a baby and name them
3. The effects are MASSIVE

Some names increased by over 1,500%! Thousands of parents chose names influenced by characters. This isn't subtle - it's a major cultural phenomenon.

4. This has been happening for over 100 years

I found examples from:

1910s (Billy, Elwood)
1950s (Liz, Vanessa)
1990s (Gage, Peyton)
2000s (Cadence, Bentley)
Fictional characters have been influencing baby names for generations!

5. It's widespread

Analyzed 3,816 different names
1,471 showed increases (38.5%)
This affects thousands of families
Why This Matters
This project shows that:

Movies and TV shows have real-world impact on personal decisions
Cultural trends can be measured and predicted
Fictional characters become part of our actual lives in measurable ways
Limitations
Can't prove 100% causation (maybe other factors involved)
Some character releases might be missing from the dataset
Splitting names might have counted some matches that weren't real influences
Didn't look at differences between movies vs TV, or different genres
Future Ideas
Things I'd like to explore:

Does box office success correlate with bigger naming effects?
Are certain genres (like romance or fantasy) more influential?
What about regional differences in the US?
Can we predict which character names will become popular?
Visualizations Generated
I created several plots to visualize these patterns:

Distribution charts showing how the % changes shift from negative (year 1) to super positive (year 5)
Bar charts of average changes over time
Time series plots of individual names with markers showing when characters appeared
Case study plots for the top influenced names

References
US Baby Names Dataset (Kaggle)
CMU Movie Summary Corpus
Summary
Bottom line: Fictional characters have a real, measurable, and massive influence on what people name their babies. The effect takes a few years to show up, but when it does, it's huge - we're talking hundreds or even thousands of percent increases for popular character names. This has been happening for over 100 years and affects thousands of families. Pretty cool to see fiction influencing reality in such a concrete way!

