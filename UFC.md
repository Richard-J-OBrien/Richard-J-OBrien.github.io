### Purpose:

The purpose of this project is to allow users to derive insights from UFC data that may aid in their improvement.

To fulfill this purpose UFC data will be gathered, visualized, and analyzed to draw general insights. Varying levels of detail will be added to allow users to perform comparisons between individual fighters and weightclasses.

---
#### Pulling UFC Data

The first step in the process is to gather the UFC data: 
- [Webscraping UFC Data](https://richard-j-obrien.github.io/2020-03-21-1-UFC-Webscraper-Report/).

---
#### Exploratory Data Analysis

---
##### Descriptive Statistical Analysis
Beginning the exploratory data analysis with visualizations, I generated several dashboards that offer varying perspectives and detail.
  
- [UFC Career Statistics Breakdown](https://public.tableau.com/profile/richard2368#!/vizhome/UFCCareerStatisticsBreakdown/Dashboard1)

- [UFC Individual Fighter Statistics Breakdown](https://public.tableau.com/profile/richard2368#!/vizhome/UFCFighterCareerStatisticsBreakdown/Individualvs_WeightClass)

- [UFC Fights: A Historical Perspective](https://public.tableau.com/profile/richard2368#!/vizhome/UFCHistoricalPerspective/Dashboard1)
  

---
##### Advanced Statistical Analysis
Considering more of the descriptive statistics have been visualized and presented in the Tableau dashboards I decided to conduct some more advanced statistical analysis. My first step was to begin to understand the relationships at the career level. Looking at all individuals career statistics across all weightclasses, I applied a correlation to determine the strength and direction of the relationships between fight statistics (e.g., strike accuracy, takedown defence, etc.).

- [UFC Career Statistics Correlations](https://richard-j-obrien.github.io/2020-04-18-Advanced-Statistics-Analysis-Part-1/)
  

---
#### Extras

I decided to test out the "highcharter" package in R too see if it would be feasible to make some nice interactive visuals with the UFC data: [UFC visuals](https://richard-j-obrien.github.io/2020-03-24-Interactive-Highcharter/). While highcharter is a great package, it didn't seem feasible to spend that much time generating all the visuals I wanted.

