Here's where I showcase the different parts of my thesis

---
#### Previous Simulation Analysis/Visualization Code - R
This code represents my initial attempt to build a simulation experiment. I broke down the code into two sections, the first focusing on the Type-I error rate and the second focusing on the Type-II error rate/Power.

- [Old Simulation Procedure - Type I Error](https://richard-j-obrien.github.io/2020-02-29-Old-Simulation-Type-I-Error/)
- [Old Simulation Procedure - Type II Error](https://richard-j-obrien.github.io/2020-02-29-Old-Simulation-Type-II-Error/)

---
#### Previous Simulation Results - Tableau
Initially I developed a simulation experiment that used average ERP waveforms as the population dataset.
- [Old Simulation Results - Average ERP Waveforms](https://richard-j-obrien.github.io/2020-03-23-Simulation-Results-Using-Average-ERP-Waveforms/)

---
#### Visualizing the Experimental Methodology - R
Following some feedback I went back to the drawing board to develop a new simulation methodology that would use a population dataset containing single trials.

- [Methodology Visualization](https://richard-j-obrien.github.io/2020-03-20-Methodology-Visualization/)

---
#### Simulation Code - Matlab
I then started to focus on building the simulation code in Matlab that will be used to generate the results of the experiment.

- [Stimulus-Locked ERP Simulation Code](https://richard-j-obrien.github.io/2020-03-24-Stimulus-Locked-Average-ERP/)


---
At this point in time I'm testing whether the simulation code works properly.

#### Analysis/Visualization Code - R

In "simulation procedures v3.0 & v3.1", I was loading thousands of csv files into R to generate the visualizations and analysis.

- [Simulation Procedure v3.0](https://richard-j-obrien.github.io/2020-03-25-New-Simulation-Procedure-v3.0/)
  - stimulus-locked averaging methodology data only
  
- [Simulation Procedure v3.1](https://richard-j-obrien.github.io/2020-03-26-New-Simulation-Procedure-v3.1/)
  - stimulus-locked averaging methodology data only

---

{: .box-note}
**Notes:** In "simulation procedure v4.0 & v4.1", I merged all csv files into one large csv file using the command prompt: *copy *.csv merged.csv*. When loaded into R, this merged.csv file is ~ 96 million rows. The population data contains ~ 1800 single trials. It might be worthwhile to reduce the population data size to ~ 1500 single trials to see how the distributions change.


- [Simulation Procedure v4.0](https://richard-j-obrien.github.io/2020-03-28-New-Simulation-Procedure-v4.0/)
  - ~1800 single trials 
  - 20 participants 
  - adding a standardized effect size (e.g., 0.5 microvolts for each 0.1 increase in effect size)
  - stimulus-locked averaging methodology data only
  
- [Simulation Procedure v4.1](https://richard-j-obrien.github.io/2020-03-28-New-Simulation-Procedure-v4.1/)
  - ~1800 single trials 
  - 20 participants 
  - adding a standardized effect size generated using the population data's standard deviation
  - stimulus-locked averaging methodology data only

---

{: .box-note}
**Notes:** In "simulation procedure v5.0", I'm going to add a few tables to understand the anova distributions. I may try to visualize this data in Tableau.


#### Simulation Results - Tableau
After running the most recent simulation procedure (v4.0), I visualized the distirbutions of the P3 amplitudes and p-values.



---

{: .box-note}
**Notes:** In the *P3 Distribution with Overlapping Conditions* dashboard I noticed that I was generating a control condition for each of the effect sizes when really I only needed one control condition, that being, the one generated using an effect size of 0. To fix this issue I simply deleted the other control conditions being produced by effect sizes 0.1 and up.


---
#### Simulation Code - Matlab
After completing the simulation code to produce the stimulus-locked ERP data and testing the whether the results made sense generally, I moved on to complete the simulation code to produce the RIDE ERP data.

- [RIDE ERP Simulation Code]()


---





