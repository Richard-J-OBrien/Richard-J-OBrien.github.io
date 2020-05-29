### Purpose:

The purpose of this project is to allow users to derive insights from UFC data and improve their understanding of the sport from a statistical perspective.

To fulfill this purpose UFC data will be gathered, visualized, and analyzed to draw general insights. Varying levels of detail will be added to allow users to perform comparisons between individual fighters and weightclasses.

---
#### Pulling UFC Data

The first step in the process is to gather the UFC data: 
- [Webscraping UFC Data](https://richard-j-obrien.github.io/2020-03-21-1-UFC-Webscraper-Report/).

---
#### Exploratory Data Analysis

---
##### Descriptive Statistical Analysis
Beginning the exploratory data analysis with visualizations, several dashboards have been produced to offer varying perspectives (e.g., from an individual and weightclass perspective).
  
- [UFC Individual Fighter Statistics Breakdown](https://public.tableau.com/profile/richard2368#!/vizhome/UFCFighterCareerStatisticsBreakdownv2_0/Individualvs_WeightClass)

- [UFC Fights: A Historical Perspective](https://public.tableau.com/profile/richard2368#!/vizhome/UFCHistoricalPerspectivev2_0/UFCFinishesOverTime)
  

---
##### Advanced Statistical Analysis
Considering more of the descriptive statistics have been visualized and presented in the Tableau dashboards, advanced statistical analysis was conducted. A correlation analysis was chosen to examinine strength and direction of the relationship between fight metrics (e.g., strike accuracy, takedown defence, etc.) within a given weightclass.


- [UFC Career Statistics Correlations](https://richard-j-obrien.github.io/2020-04-18-Advanced-Statistics-Analysis-Part-1/)
  

---
#### Extras

I decided to test out the "highcharter" package in R too see if it would be feasible to make some nice interactive visuals with the UFC data: [UFC visuals](https://richard-j-obrien.github.io/2020-03-24-Interactive-Highcharter/). While highcharter is a great package, it didn't seem feasible to spend that much time generating all the visuals I wanted.

