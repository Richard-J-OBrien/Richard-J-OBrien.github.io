---
title: "Methodology Rationale and Visualization"
author: "Richard O'Brien"
date: "November 30th, 2019"
output:
  html_document:
    chunk_output_type: console
    code_folding: hide
    editor_options:
      chunk_output_type: console
    keep_md: yes
    theme: lumen
---




###Study Rationale & Impact

<br>

Due to the sensitivity of EEG, ERP data is not ready for immediate analysis following data collection because noise exists. Generally speaking, ERP data needs to be pre-processed using artifact rejection and averaging methodologies to remove noise. Following the pre-processing, peak-picking methodologies are applied to quantify ERP components. Each of these steps, artifact rejection, averaging, and peak-picking, can reduce the prevalence and influence of noise on the ERP components. Guidelines and recommendations for removing noise, identifying, and measuring ERP components have been established to aid researchers in determining which techniques are appropriate for their data (Picton et al., 2000; Keil et al., 2014). At the moment though, the variety of artifact rejection, averaging, and peak-picking methodologies commonly being used means that it is not well known how researchers methodological selections (artifact rejection, averaging, peak-picking) influence their ability to detect changes in cognitive functioning. 

Conventionally, an artifact rejection methodology is chosen to remove noise from the data before single trial waveforms are averaged together. The removal of artifacts (noise) from the single trials plays an integral part in reducing the likelihood of spurious results, and aims to improve the signal to noise ratio (Luck, 2014). Noise artifacts can often be seen as large distortions in the ERP signals, and may be systematic in nature (Luck, 2014). The process of removing noise is helpful in terms of improving the quality of the data, but no noise removal process will replace the effort to minimize noise during collection (Luck, 2014).

Following the removal of noise from the single trial waveforms via artifact rejection, an averaging methodology can be applied. ERP averaging results in a loss of information, although this is not inherently negative if noise is removed. Averaging aims to represent single trial waveforms while reducing the prevalence of noise further (Luck, 2014). A variety of averaging methodologies have been utilized. Simple averaging methodologies have aligned single trials to the stimulus or response (Luck, 2014), while more complex averaging methodologies have binned single trials based on reaction times (Poli et al., 2010) or aligned sections of the single trial waveform before averaging (Ouyang et al., 2011). These averaging methodologies can moderate ERP components shape and size, representing the single trial waveforms and ERP components more or less accurately. Despite selecting and applying an averaging methodology, noise may remain within the ERP waveform, potentially causing the peak-picking methodologies to be biased.

Common ERP peak-picking methodologies have been examined by researchers more recently (Clayson et al., 2013; Nielsen & Gonzalez, 2019), and the evidence indicates that in recent years, the mean methodology is most commonly used, followed by the peak methodology, and least commonly the adaptive mean methodology (Clayson et al., 2013). Given that researchers can choose any peak-picking methodology, it has become increasingly important to understand how these peak-picking methodologies are influenced by noise and other factors.

Noise within the average ERP waveform can be a highly influential factor when quantifying ERP components. Noise can impact a peak-picking methodology's bias and efficiency (Clayson et al., 2013). Comparing peak-picking methodologies (peak, mean, adaptive mean) under various noise conditions, it was determined that the peak amplitude methodology should be avoided due to its increase in bias and decrease in efficiency as noise increases (Clayson et al., 2013). In contrast, the mean methodology provided the best performance (Clayson et al., 2013). Noise can also be minimized by ensuring average ERP waveforms are generated from at least 30 single trials  (Clayson et al., 2013).

The comparison of these peak-picking methodologies was extended to examine whether differences in the peak latencies, time window length, and trial count, would impact type-I and II error rates (Neilsen and Gonzalez, 2019). The peak methodology appeared to underperform when the number of trials differed across conditions, no latency differences existed between conditions, and data contains noise (Neilsen & Gonzalez, 2019). The adaptive mean methodology seemed to be slightly more robust compared to the peak methodology, but the mean methodology tended to produce higher type-I and II error rates under low and high latency variability (Neilsen and Gonzalez, 2019). Increasing the time window does not reduce the type-I error rates of the mean amplitude either (Neilsen and Gonzalez, 2019). It could not be concluded that one peak-picking methodology was better than the others (Neilsen and Gonzalez, 2019). Instead, it was suggested that the justification and description of each methodology in the ERP analysis pipeline be documented so that researchers could compare their results to alternate methodologies in the future (Neilsen and Gonzalez, 2019).

Given the variety of artifact rejection, averaging, and peak-picking methodologies currently being used, and the influence of factors such as noise, intra-subject variability, and single trial count, it is still unclear as to how a researcher's set of methodological selections (artifact rejection, averaging, peak-picking) may influence their ability to detect changes in cognitive functioning. With this study, I aim to evaluate and determine which common peak-picking methodology (peak, mean, and adaptive mean) and averaging methodologies (stimulus-locked, RIDE) provide the most sensitivity (power to detect a true difference) and specificity (correct classification of null effects) under varying experimental scenarios (sample and effect size). 

###Study Purpose
<br>

The overarching purpose of this thesis is to assess the statistical properties of common and novel averaging and peak identification approaches in order to understand their utility under different experimental settings (sample and effect size), and determine whether these methodologies enhance the ability to detect changes in cognitive functioning. 
	
The present study plans to extend the work of Clayson and colleagues (2013) and Neilsen & Gonzalez (2019) in several different ways. In this study, the influence of multiple sample sizes, effect sizes, and averaging methodologies will be factored in. While other researchers have included sample sizes in their designs, sample sizes have been used to examine noise levels and the use of unbalanced conditions (Clayson et al., 2013; Neilsen & Gonzalez, 2019). In this study, manipulating single trial samples sizes allows for the evaluation of this factor on each peak-picking methodologies sensitivity and specificity, and whether averaging methodologies can meaningfully moderate the statistical power and error rates. Including effect sizes also provides more detail on how the averaging and peak-picking methodologies moderate the measures of interest across conditions with known differences. The addition of a novel averaging methodology aims to determine whether the process of aligning the P3 component before averaging can improve representativeness of the P3 amplitude and the ability to detect true differences between conditions compared to the typical stimulus-locked average methodology. Overall, the evaluation of these averaging and peak-picking methodologies under several experimental conditions (sample and effect sizes), aims to compare their ability to handle noise and intra-subject variability, and indicate the conditions where the minimum necessary statistical power is produced. 


<br>

###Methodology Diagram

<br>

Objectives:

1. To compare the sensitivity (power to detect a true difference) and specificity (correct classification of null effects) of ERP peak-picking methodologies (peak, adaptive mean, and mean) in detecting a range of effect sizes in a range of sample sizes (for single trials).

2. To compare the sensitivity and specificity of two ERP averaging methodologies (stimulus-locked and RIDE) in detecting a range of effect sizes in a range of sample sizes (for single trials).

<br>

Run following procedure 1000 times

Step 1: The population dataset is comprised of single trials

Step 2: Use the sample size (10 to 100, in increments of 10) to randomly sample without replacement from the population dataset.

Step 3: Assign the sampled single trials to the control and experimental condition and apply the effect size to the single trials in the experimental condition

Step 4: 

a) Calculate the average ERP waveform using the stimulus-locked methodology
b) Calculate the average ERP waveform using the RIDE methodology

Step 5: Produce 20 average waveforms for each averaging methodology. 

Step 6: Calculate the P3 amplitudes of each average ERP waveform in each condition using the peak-picking methodologies (peak, mean, adaptive mean)

Step 7: Calculate an ANOVA to determine whether a statistically significant difference is present between the control and experimental conditions P3 amplitudes

Step 8: Calculate the power, type-I error rate, P3 means and sds



```r
pkgTest <- function(...) {
  pkg <- list(...)
  for (i in 1:length(pkg)) {
    if (!require(pkg[[i]], character.only = TRUE)) {
      install.packages(pkg[[i]], dep = TRUE)
      if(!require(pkg[[i]], character.only = TRUE)) stop("Package not found")
    } 
  }
}


pkgTest("collapsibleTree")
```

```
## Loading required package: collapsibleTree
```

```r
org <- data.frame(
  Manager = c(
  NA,
  "Single Trial Pop. Dataset",
  "Single Trial Pop. Dataset",
  "Experimental",
  "Experimental",
  "Control",
  "Control",
  "Stimulus-Locked Avg ERPs",
  "RIDE Avg ERPs",
  "Stimulus-Locked Avg ERPs",
  "RIDE Avg ERPs",
  "Stimulus-Locked Avg ERPs",
  "RIDE Avg ERPs"
  ),
  Employee = c(
  "Single Trial Pop. Dataset",
  "Experimental",
  "Control",
  "Stimulus-Locked Avg ERPs",
  "RIDE Avg ERPs",
  "Stimulus-Locked Avg ERPs",
  "RIDE Avg ERPs",
  "Peak Amplitude",
  "Peak Amplitude",
  "Mean Amplitude",
  "Mean Amplitude",
  "Adaptive Mean Amplitude",
  "Adaptive Mean Amplitude"
  ),
  Program = c(
  "Matlab",
  "Matlab",
  "Matlab",
  "Matlab",
  "Matlab",
  "Matlab",
  "Matlab",
  "R",
  "R",
  "R",
  "R",
  "R",
  "R"
  )
  )



collapsibleTreeNetwork(org, 
                       attribute = "Program",
                       width = 1000,
                       linkLength = 200,
                       zoomable = FALSE,
                       fontSize = 12,
                       collapsed = FALSE)
```

<!--html_preserve--><div id="htmlwidget-20a94fc7e4d7b9a7cdce" style="width:1000px;height:480px;" class="collapsibleTree html-widget"></div>
<script type="application/json" data-for="htmlwidget-20a94fc7e4d7b9a7cdce">{"x":{"data":{"name":"Single Trial Pop. Dataset","WeightOfNode":"Matlab","children":[{"name":"Experimental","WeightOfNode":"Matlab","children":[{"name":"Stimulus-Locked Avg ERPs","WeightOfNode":"Matlab","children":[{"name":"Peak Amplitude","WeightOfNode":"R"},{"name":"Mean Amplitude","WeightOfNode":"R"},{"name":"Adaptive Mean Amplitude","WeightOfNode":"R"}]},{"name":"RIDE Avg ERPs","WeightOfNode":"Matlab","children":[{"name":"Peak Amplitude","WeightOfNode":"R"},{"name":"Mean Amplitude","WeightOfNode":"R"},{"name":"Adaptive Mean Amplitude","WeightOfNode":"R"}]}]},{"name":"Control","WeightOfNode":"Matlab","children":[{"name":"Stimulus-Locked Avg ERPs","WeightOfNode":"Matlab","children":[{"name":"Peak Amplitude","WeightOfNode":"R"},{"name":"Mean Amplitude","WeightOfNode":"R"},{"name":"Adaptive Mean Amplitude","WeightOfNode":"R"}]},{"name":"RIDE Avg ERPs","WeightOfNode":"Matlab","children":[{"name":"Peak Amplitude","WeightOfNode":"R"},{"name":"Mean Amplitude","WeightOfNode":"R"},{"name":"Adaptive Mean Amplitude","WeightOfNode":"R"}]}]}]},"options":{"hierarchy":[1,2,3,4],"input":null,"attribute":"Program","linkLength":200,"fontSize":12,"tooltip":true,"collapsed":false,"zoomable":false,"margin":{"top":20,"bottom":20,"left":175,"right":163},"fill":"lightsteelblue"}},"evals":[],"jsHooks":[]}</script><!--/html_preserve-->


###References

Kristopher Beyer (2018). Cognitive control, conflict monitoring, and aerobic exercise.. UWSpace. http://hdl.handle.net/10012/13217

Clayson, P. E., Baldwin, S. A., & Larson, M. J. (2013). How does noise affect amplitude and latency measurement of event-related potentials (ERPs)? A methodological critique and simulation study. Psychophysiology, 50(2), 174-186.

Luck, S. J. (2014). An introduction to the event-related potential technique, Second Edition. MIT press.

Keil, A., Debener, S., Gratton, G., Junghöfer, M., Kappenman, E. S., Luck, S. J., ... & Yee, C. M. (2014). Committee report: publication guidelines and recommendations for studies using electroencephalography and magnetoencephalography. Psychophysiology, 51(1), 1-21.

Poli, R., Cinel, C., Citi, L., & Sepulveda, F. (2010). Reaction-time binning: A simple method for increasing the resolving power of ERP averages. Psychophysiology, 47(3), 467-485.

Picton, T. W., Bentin, S., Berg, P., Donchin, E., Hillyard, S. A., Johnson, R., ... & Taylor, M. J. (2000). Guidelines for using human event-related potentials to study cognition: recording standards and publication criteria. Psychophysiology, 37(2), 127-152.

Nielsen, K., & Gonzalez, R. (2019). Comparison of Common Amplitude Metrics in Event-Related Potential Analysis. Multivariate behavioral research, 1-16.

Ouyang, G., Herzmann, G., Zhou, C., & Sommer, W. (2011). Residue iteration decomposition (RIDE): A new method to separate ERP components on the basis of latency variability in single trials. Psychophysiology, 48(12), 1631-1647.
