Advanced Statistics Module 10 - Introduction to ANOVA
================

Introduction to ANOVA
=====================

"A researcher is interested in the effects of drug against stress reaction. She gives a reaction time test to three different groups of subjects: one group that is under a great deal of stress, one group under a moderate amount of stress, and a third group that is under almost no stress. The subjects of the study were instructed to take the drug test during their next stress episode and to report their stress on a scale of 1 to 10 (10 being most pain)."

``` r
library(readxl)
Stress_data <- read_excel("C:/Users/adamw/Documents/Advanced Statistics/Stress data.xlsx")
```

First we initialize and calculate the data using an analysis of variance test. For this calculation, I assigned each individual a corresponding number (1,2 or 3) indicating their stress group. 1 is High, 2 is Moderate and 3 is Low.

``` r
aov = aov(Stress_data$`Stress Group`~Stress_data$`Stress Level`)
summary(aov)
```

    ##                            Df Sum Sq Mean Sq F value   Pr(>F)    
    ## Stress_data$`Stress Level`  1  8.112   8.112   33.38 2.83e-05 ***
    ## Residuals                  16  3.888   0.243                     
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

For the first test, we compare the stress levels compared to each group. Our null hypothesis in this case would be that there is no correlation between the pain level of individuals relative to which group they are in, while the alternative hypothesis is that there is a correlation. From the results, we see that the p value is quite small, .0000283 to be exact, so we can reject the null hypothesis and conclude that there is a correlation between pain level and stress level.

We can also see here that our degree of freedom is 16, the squared sum of variation is 3.888 with a mean variation of .243, and our f-value is 33.38, which means the variation in our data set is quite high. This is likely because of the small sample size (n) value.
