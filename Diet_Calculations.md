Diet calculations
================
Wynes
March 4, 2018

Food calculations use life cycle emissions as presented in Heller et al. (2013). For instance, beef is 29kgCO2e/kg beef or Hoolohan (2013)

\*\*ABRAHAMSE ET AL. 2007

Using the values from Hoolohan et al. (2013) for weighted average of meat (processed and cooked) of 13.61kgCO2eq/kg and assuming replacement by vegetarian meat alternatives (at 4.81kgCO2eq/kg) gives 8.8kgCO2eq/kg of meat

``` r
104-97 #These are the reductions seen in the control group
```

    ## [1] 7

``` r
meat_reduc <- 101-92-7 #Reductions seen in the intervention group - control group reductions

meat_reduc*8.8*365*3 #Assume three meals a day for one year
```

    ## [1] 19272

``` r
meat_reduc
```

    ## [1] 2

The intervention reduces emissions by 19kgCO2e per year.

\*\*BRUNNER ET AL. 2018 The design of this experiment is rather complicated with the intervention impact assessed over a time period with a changing menu. The authors provide an expected average emissions for food with three different labels and the actual average emissions calculated after the intervention. To find the effect of the intervention we use "Expected Label" - "Label". Due to a lack of information on what portion of emissions come from red, green or yellow labelled meals we take only the red, which provides a generous estimate of effect.

``` r
#Expected Label
red <- 3.55-3.34 #Values taken from Figure 6
red*48*5
```

    ## [1] 50.4

Average emissions saved per meal are therefore 0.21kgCO2e. Over the course of a year (assuming 48 work weeks of visiting the cafeteria and 5 meals a week) this would create emissions reductions of 50.4kgCO2e per year.

\*\*CARFORA ET AL. 2017 Carfora defines 2 medium portions as 200g. We therefore take their reported portions per week and multiply by 100g per portion. We assume substitution of red meat - average of beef 25.13kgCO2e/kg and pork 10.29kgCO2e/kg (17.71kgCO2e/kg) by poultry (4.05kgCO2e/kg) for a difference of 13.66kgCO2e/kg (since unlike Klockner they emphasize not reducing meat by reducing red meat)

CONTROL MEAN DECREASE PER WEEK

``` r
#Mean decrease from T1 to T2
control_mean_decrease <- 3.26-3.03
control_mean_decrease
```

    ## [1] 0.23

0.23 servings of red meat reduction per week in the control

SMS MEAN DECREASE PER WEEK

``` r
SMS_mean_decrease <- 13.66*100*(3.13-1.62-0.23) #Subtract control, multiply by 100g/serving and by emissions factor
SMS_mean_decrease
```

    ## [1] 1748.48

``` r
SMS_mean_decrease*52 #Find mean annual emissions reduction
```

    ## [1] 90920.96

``` r
100*(3.13-1.74-0.23)
```

    ## [1] 116

Mean red meat reduction of 116g per week compared to control Mean red meat emissions reduction of 90.92kgCO2e/year (p&lt;0.001)

\*\*FRIIS ET AL. 2017 Assume 1/3 recipe is beef based on recipe from: <https://www.bbcgoodfood.com/recipes/3228/chilli-con-carne> (authors did not reply to email clarifying recipe)

Default group, con carne decreases by 17.54g = 5.85g beef x 29gCO2e = 169.65gCO2e p =0.41 Priming group, con carne decreases by 115.59g = 38.53g beef x29gCO2e = 1117.37gCO2e p&lt;0.01 Perceived variety group, con carne decreases by 82.67g = 27.56g of beef = 779.14gCO2e p&lt;0.01

Because food intake decreases for the priming and preceived variety group, mostly due to drops in con carne, we do not account for increases in other foods, and simply account for decrease in beef emissions. Decrease in the default group was not significant.

``` r
Default<-17.51/3*29/1000
Default*48*5
```

    ## [1] 40.6232

``` r
Priming<- 115.59/3*29/1000
Priming*48*5
```

    ## [1] 268.1688

``` r
Perceived<- 82.67/3*29/1000
Perceived
```

    ## [1] 0.7991433

``` r
Perceived*48*5
```

    ## [1] 191.7944

Assuming one meal, five times a day, and 48 weeks of work creates emissions reductions of 40.62kg for the default group, 268.17kgCO2e for the priming group and 191.79kgCO2e for the perceived variety group over the year.

Notes: Took place in a lab that reproduced the settings of a campus canteen. The researchers measured consumption minus wastage whereas our ideal measurement would just be consumption. Benefited from actual instead of self-reported measurements. Subjects may have adjusted behavior from being aware that they were being studied.

\*\*KLOCKNER & OFSTAD 2017 In the paper Klockner suggest that "Study 2" may be subject to bias due to an extremely low response rate, and instead view Study 3 as more reliable. We therefore draw results from Study 3, comparing intervention groups to the control group. We assume that beef consumption is replaced by vegetarian meat alternatives (25.13-4.81=20.32kgCO2e/kg beef reduced)

``` r
#MEAN TAILORED INFO MINUS CONTROL
#The control group decreased beef consumption by 37.803g/week
-24.169 - (-37.803)
```

    ## [1] 13.634

``` r
mean_tailor <- 20.32*(-24.169 - (-37.803))
mean_tailor*52
```

    ## [1] 14406.23

Tailored group increased beef consumption by 13.63g beef per week increased emissions by 277gCO2e/week or 14.41kgCO2e/year

``` r
#MEAN ALL INFO MINUS CONTROL
(72.417 - (-37.803))
```

    ## [1] 110.22

``` r
mean_allinfo <- 20.32*(72.417 - (-37.803))
mean_allinfo
```

    ## [1] 2239.67

``` r
2239.67*52
```

    ## [1] 116462.8

The all information group increased beef consumption by 110.22gCO2e/week and increased emissions by 2.24kgCO2e/week or 116.46kgCO2e/year

``` r
#MEAN RANDOM MINUS MEAN CONTROL
(-14.236- (-37.803))
```

    ## [1] 23.567

``` r
mean_random <- 20.32*(-14.236- (-37.803))
mean_random*52
```

    ## [1] 24901.83

The random information group increased beef consumption by 23.57g/week increased CO2e by 478.88g/week or 24.90kgCO2e/year

Only the all information group changed by a significant amount compared to the control group (and it increased beef consumption with a result of 2.24kgCO2e increasing per WEEK).

\*\*LOY ET AL. 2016 Information only (control) reduced consumption of meat by 27g at the second follow-up (39.4 standard deviation). N=28

Using the values from Hoolohan et al. (2013) for weighted average of meat (processed and cooked) of 13.61kgCO2eq/kg and assuming replacement by vegetarian meat alternatives (at 4.81kgCO2eq/kg) gives 8.8kgCO2eq/kg of meat. Although the control group is itself a type of intervention (information provided to discourage meat consumption) we subtract control from intervention so that we can also report the study's measure of significance, thereby providing a conservative estimate.

Intervention reduced meat by 50.3g in the 2nd follow-up period

INTERVENTION SECOND FOLLOWUP

``` r
 a <- 50.3 - 27 #Intervention - Control

 a*8.8
```

    ## [1] 205.04

``` r
 a*8.8*365
```

    ## [1] 74839.6

INTERVENTION FOLLOWUP 2 mean = 205gCO2/meal mean = 74.8kgCO2/year (p&lt;0.05 compared to control)
