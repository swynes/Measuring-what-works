Household\_calculations
================
Wynes
March 27, 2018

\*\*Assumptions 1679.3lbs/MWh is the maximum emissions from a subregion in the US while 295.9lbs/MWh is the minimum, and the US overall is 1004.2 lbs/MWh (eGRID2016 SUMMARY). We take this as reasonable upper and lower ranges for energy intensity.

We therefore use an average intensity of 0.455kgCO2e/kWh maximum intensity of 0.762kgCO2e/kWh and a minimum of 0.134kgCO2e/kWh

``` r
max_int <- 0.762
min_int <- 0.134
avg_int <- 0.455
```

\*\*ALBERINI & TOWE 2015

When performing greenhouse gas calculations for the energy audit, a baseline of 18000KWh per year is assumed by the authors, and with 5% reduction in energy use this leads to 900KWh reduction per year (significant). For the rebate on the heat pump a baseline of 21000KWh is provided (savings of 1050KWh per year). Because they run several models (coarsened exact matching or CEM) to match experimental households with households that have similar characteristics in the control sample there are several levels of significance provided. However those that are provided for the CEMs that result in 5% reductions are reported as "statistically significant at the conventional levels" for the audit and "strongly statistically significant" for the heat pump.

``` r
e_audit <- 18000*0.05 #KWh saved by energy audit
pump_rebate <- 21000*0.05 #KWh saved by rebate on heat pump

e_audit*max_int
```

    ## [1] 685.8

``` r
e_audit*min_int
```

    ## [1] 120.6

``` r
e_audit*avg_int
```

    ## [1] 409.5

``` r
pump_rebate*max_int
```

    ## [1] 800.1

``` r
pump_rebate*min_int
```

    ## [1] 140.7

``` r
pump_rebate*avg_int
```

    ## [1] 477.75

The energy audit therefore leads to savings of 409.5kgCO2e/year range of 120.6-685.8kgCO2e/year (p&lt;0.05) The pump rebate leads to savings of 477.8kgCO2e/year range of 140.7-800.1kg/year (p&lt;0.01)

\*\*ALLCOTT 2011

A treatment group is mailed feedback with a peer comparison, injunctive norm and tips on conservation while the control is not mailed anything. The average treatment effect is 2% or 0.62KWh reduced per day. The average treatment effects are described as significant, but there is nuance shown in Section 3.2 and Table 3 as many different experiments were run.

``` r
0.62*365*min_int  #Calculate emissions saved per year
```

    ## [1] 30.3242

``` r
0.62*365*max_int
```

    ## [1] 172.4406

``` r
0.62*365*avg_int
```

    ## [1] 102.9665

The treatment reduces emissions by 102.97kgCO2e/year or range of 30.32-172.44kgCO2e/year

\*\*ASENSIO & DELMAS 2015

Health and environmental based feedback versus monetary feedback compared to a control group. Table S10 in the Supplemental provides Average kWh usage/day.

Treatment 1 (Monetary Savings): 7.543KWh/day Treatment 2 (Health and Environment Messaging): 7.457KWh/day

The monetary group shows a 3.8% increase in energy use compared to the control (not significant). The health group shows an 8.2% decrease in energy use compared to the control (significant p&lt;0.05)

``` r
Monetary <- 7.453*0.038 #Find KWh increased per day
Health <- 7.457*0.082 #Find KWh saved per day

Monetary*365*min_int #Find emissions increased per year
```

    ## [1] 13.852

``` r
Monetary*365*max_int
```

    ## [1] 78.77031

``` r
Monetary*365*avg_int
```

    ## [1] 47.03477

``` r
Health*365*min_int #Find emissions saved per year
```

    ## [1] 29.90719

``` r
Health*365*max_int
```

    ## [1] 170.0693

``` r
Health*365*avg_int
```

    ## [1] 101.5505

The monetary group increases energy by 0.3kWh/day or 13.9-78.8kgCO2e increased per year. The Health group decreases energy use by 0.6kWh/day or 29.9-170.1kgCO2e decreased per year.

\*\*AYRES ET AL. 2013

In the SMUD group the intervention group is given peer feedback and normative messages (smiley faces for low energy usage). They estimate savings of 187.20KWh per year

``` r
187.20*max_int
```

    ## [1] 142.6464

``` r
187.20*min_int
```

    ## [1] 25.0848

``` r
187.20*avg_int
```

    ## [1] 85.176

``` r
187.20/365
```

    ## [1] 0.5128767

Annual reductions of 85.18kgCO2e or range of 25.08-142.65kgCO2e. Reductions are significant for each week after the treatment (not immediately obvious which level of significance to associate with this value as it is a weighting of quarterly and monthly experiments)

In the PSE group they estimate savings of 140.85KWh/year and 10.14therms reductions per year.

``` r
heat_saved <- 10.14*0.0053*1000 #Using 0.0053metric tons CO2 per therm (https://www.epa.gov/energy/greenhouse-gases-equivalencies-calculator-calculations-and-references)

140.85*max_int + heat_saved
```

    ## [1] 161.0697

``` r
140.85*min_int + heat_saved
```

    ## [1] 72.6159

``` r
140.85*avg_int + heat_saved
```

    ## [1] 117.8287

Therefore reductions of 117.83kgCO2e/year or a range of 72.62-161.07CO2e/year. There are different levels of significance for different periods of time and for the therms (heat saved) and for the kWh saved in this intervention. More weeks were significant than not for both therms and kWh.

\*\*BEKKER ET AL. 2010

A treatment university residence hall received daily feedback and rewards and is compared to a control hall. The treatment hall had 190 students in single occupancy rooms, heating, hot water were not included and cooling systems were not present. Over three weeks the intervention hall saved 3700.31kWh.

``` r
3700.31/3/190 #Find kWh/week/person
```

    ## [1] 6.491772

``` r
(3700.31/3/190)*52*min_int #Find emissions reductions per person per  year
```

    ## [1] 45.23467

``` r
(3700.31/3/190)*52*max_int
```

    ## [1] 257.23

``` r
(3700.31/3/190)*52*avg_int
```

    ## [1] 153.5953

The intervention reduced energy use by 6.49kWh/person/week or 153.60kgCO2e/year with a range of 45.23-257.23kgCO2e/person/year

\*\*CARROLL ET AL. 2014 Three interventions and one control. All treatment groups also paid time of use tariffs (higher for peak hours, lower for off hours) MST: energy statement bimonthly (60.33KWh annual reductions compared to control) IHD: In-house display (43.03KWh) MST: monthly energy statement (7.13KWh) These are very low numbers considering that 60.33KWh is given as a 2.9% reduction - I contacted James Carrol to confirm, no reply.

``` r
MST <- 60.33
IHD <- 43.03
BIMST <- 7.13
BIMST * min_int
```

    ## [1] 0.95542

``` r
BIMST * max_int
```

    ## [1] 5.43306

``` r
BIMST * avg_int
```

    ## [1] 3.24415

``` r
MST * min_int
```

    ## [1] 8.08422

``` r
MST * max_int
```

    ## [1] 45.97146

``` r
MST * avg_int
```

    ## [1] 27.45015

``` r
IHD * min_int
```

    ## [1] 5.76602

``` r
IHD * max_int
```

    ## [1] 32.78886

``` r
IHD * avg_int
```

    ## [1] 19.57865

MST saves 27.45kgCO2e/year or from 8.08-45.97kgCO2e per year (significant at p&lt;0.01) IHD saves 19.58kgCO2e/year or range of 5.77-32.79kgCO2e per year (significant at p&lt;0.05) BIMST saves 3.24kgCO2e/year or range of 0.96-5.43kgCO2e per year (not significant)

COSTA & KAHN 2013

The treatment group used an average of 30.801KWh/day The overall treatment effect is 2.1% Significance at p&lt;0.05

``` r
0.021*30.801
```

    ## [1] 0.646821

``` r
0.021*30.801*356*max_int
```

    ## [1] 175.4644

``` r
0.021*30.801*356*min_int
```

    ## [1] 30.85595

``` r
0.021*30.801*356*avg_int
```

    ## [1] 104.7721

Annual reductions from overall treatment estimated at 104.77kgCO2e/year with range from 30.85-175.46kgCO2e

DELMAS & LESSEM 2014

One treatment received feedback on their rooms energy usage (including a peer comparison), the other received feedback and then in later weeks their room's relative energy use was publicly displayed.

Private information reduces energy use by 441.692Wh/day Public information reduces energy use by 1504.371Wh/day (p&lt;0.05)

``` r
#Private feedback
0.441692*365*min_int #Find annual emissions
```

    ## [1] 21.60316

``` r
0.441692*365*max_int
```

    ## [1] 122.8478

``` r
0.441692*365*avg_int
```

    ## [1] 73.354

``` r
1.504371*365*min_int #Find annual emissions for public information
```

    ## [1] 73.57879

``` r
1.504371*365*max_int 
```

    ## [1] 418.4107

``` r
1.504371*365*avg_int 
```

    ## [1] 249.8384

The private feedback results in 73.35kgCO2e or a range of 21.60-122.85kgCO2e reduced per year (not significant) The public feedback results in 249.84kgCO2e/year or range of 73.58-418.41kgCO2e reduced per year (p&lt;0.05)

GLEERUP ET AL. 2010 - Gleerup et al. have three treatment groups. They only explicitly report KWh in the text for the third treatment group (the first treatment group was subject to some technical errors so we have excluded regardless) which is what we report here. They report 135kWh reductions in treatment 3.

``` r
135*min_int
```

    ## [1] 18.09

``` r
135*max_int
```

    ## [1] 102.87

``` r
135*avg_int
```

    ## [1] 61.425

Therefore CO2e reductions are 61.43kgCO2e/year or range from 18.09-102.87kgCO2e/year (not significant).

\*\*GRONHOJ & THOGERSEN 2011 Electricity usage decreased from 5584KWh to 5133KWh in the treatment group (8.1% decrease). The control group however decreased consumption by a reported 0.8%. NOTE\* In an apparent contradiction the authors later report savings of 0.7% by the control group in the conclusion. Here we subtract the reductions made by the treatment group from that of the control group, using the 0.8% value given which results in more conservative savings for the treatment group.

``` r
#8.1-0.8=7.3% reduction
5584*0.073
```

    ## [1] 407.632

``` r
407.632*min_int
```

    ## [1] 54.62269

``` r
407.632*max_int
```

    ## [1] 310.6156

``` r
407.632*avg_int
```

    ## [1] 185.4726

Therefore the intervention reduced electricty consumption by 407.63KWh This would result in reductions of 185.47kgCO2e/year or a range of 54.62-310.62kgCO2e per year

\*\*HERTER ET AL. 2013

Treatment 1 (Baseline) given a home energy assessment, treatment 2 (Home) was also given feedback on energy use while Treatment 3 (Appliance) was also given feedback on energy use and appliance level information. No data is provided on change in the control group except that the change in the group was insignificant. We therefore only use change from previous year's consumption, adjusted by weather, as provided in Table 3. Table 3 says, "All impacts are statistically significant (p&lt;0.01)"

Baseline: -0.07KW Home: -0.12KW Appliance: -0.07KW

``` r
#Baseline
0.07*24 #multiply by 24 hours in a day
```

    ## [1] 1.68

``` r
0.12*24
```

    ## [1] 2.88

``` r
0.07*24*365*max_int
```

    ## [1] 467.2584

``` r
0.07*24*365*min_int
```

    ## [1] 82.1688

``` r
0.07*24*365*avg_int
```

    ## [1] 279.006

``` r
0.12*24*365*max_int
```

    ## [1] 801.0144

``` r
0.12*24*365*min_int
```

    ## [1] 140.8608

``` r
0.12*24*365*avg_int
```

    ## [1] 478.296

The Baseline and Appliance intervention reduce energy use by 1.68KWh per day or 279.01kgCO2e/year or range from 82.17-467.26kgCO2e/year The Home intervention reduces energy use by 2.88KWh per day or 478.30kgCO2e/year or range from 140.86-801.01kgCO2e/year

Note that as aspects of this intervention are specifically related to summer (adjusting temperature during summertime highs) so scaling up to the whole year may give misleading results.

\*\*HOUDE ET AL. 2013

Authors report that the treatment effect is 0.05kWh per hour.

``` r
0.05*24*365*min_int #Find annual emissions saved
```

    ## [1] 58.692

``` r
0.05*24*365*max_int
```

    ## [1] 333.756

``` r
0.05*24*365*avg_int
```

    ## [1] 199.29

Annual remissions reductions are therefore 199kgCO2e/year or a range of 59-334kgCO2e/year (significant at the 5% level) though authors report diminishing returns over time.

\*\*JENSEN ET AL. 2012

Treatment group (Treated) received an autopoweroff plug in the mail. Control group (Untreated) did not. The simplest approach is as follows:

``` r
Untreated <- 9.175-8.005 #Mean kWh/day during pre and post periods taken from Table 2

Treated <- 11.331-10.044-Untreated

Treated
```

    ## [1] 0.117

``` r
Treated*365*min_int
```

    ## [1] 5.72247

``` r
Treated*365*max_int
```

    ## [1] 32.54121

The treatment reduces energy by 0.117KWh/day, or 5.72-32.54kgCO2e per year

However, using their calculations for propensity score matching we have a treatment applied to four different populations: single male (150KWh reduced per year), single female (0KWh reduced per year), no children (225KWh reduced per year), children (0KWh reduced per year). It's reasonable to split up these groups because part of the logic of the paper is that interventions should be targeted at receptive populations. Furthermore in this part of the anaylsis the authors controlled for household characteristics, making the results more rigorous. We therefore use the calculations below:

``` r
150*min_int
```

    ## [1] 20.1

``` r
150*max_int
```

    ## [1] 114.3

``` r
150*avg_int
```

    ## [1] 68.25

``` r
225*min_int
```

    ## [1] 30.15

``` r
225*max_int
```

    ## [1] 171.45

``` r
225*avg_int
```

    ## [1] 102.375

Single males reduce 68.3kgCO2e/year or a range of 20.1-114.3kgCO2e/year (p&lt;0.05) Families with children reduce 102.4kgCO2e/year or a range of 30.15-171.45kgCO2e/year (p&lt;0.05) Single females and families with children reduce 0kgCO2e/year (not significant)

\*\*MARTIN & RIVERS 2018

Natural experiment where rollout of a feedback device is staggered by a utility company. The group of households who requested a device but have not yet received it act as a control and those who receive it act as a treatment . They find 3.1% reduction of the 1.2KWh per hour in the treatment group compared to the control group (a few other values for average KWh are provided - we take the most conservative).

``` r
0.031*1.2 #Determine the effect of a 3.1% reduction
```

    ## [1] 0.0372

``` r
0.0372*24*365*min_int
```

    ## [1] 43.66685

``` r
0.0372*24*365*max_int
```

    ## [1] 248.3145

``` r
0.0372*24*365*avg_int
```

    ## [1] 148.2718

The feedback intervention reduces electricity consumption by 0.0372KWh per hour or 148.27kgCO2e/year with a range of 43.67-248.31kgCO2e/year (p&lt;0.01, found in Supplementary Table B1)

\*\*MATSUKWAKA 2004

The treatment group was provided with IHD devices for electricity monitoring (no peer comparison). A model determined that daily reductions from the treatment amounted to 0.053kWh per day. Significant at the p&lt;0.01 level.

``` r
0.053*365*min_int #Find emissions savings per year
```

    ## [1] 2.59223

``` r
0.053*365*max_int #Find emissions savings per year
```

    ## [1] 14.74089

``` r
0.053*365*avg_int
```

    ## [1] 8.801975

Emissions savings per year estimated at 8.80kgCO2e/year or a range of 2.59-14.74kgCO2e/year

\*\*NILSSON ET AL. 2014

Two studies. In study 1 the treatment group received an in-house display (IHD feedback device) and control group did not. Both groups received information on how to reduce electricity, which means the effect of the treatment group is slightly reduced as the control had a type of intervention (albeit a less effective one).

``` r
Nilsson_Control <- 1634.8 - 762.7

1733.8 - 745.9  - Nilsson_Control #Difference in difference to find magnitude of treatment
```

    ## [1] 115.8

``` r
115.8*12*min_int #multiply by 12 months and emissions intensity
```

    ## [1] 186.2064

``` r
115.8*12*max_int
```

    ## [1] 1058.875

``` r
115.8*12*avg_int
```

    ## [1] 632.268

The treatment group reduced electricity use by 115.8KWh per month per household or 632.27kgCO2e/year or range of 186.21-1058.88kgCO2e/year Differences not significant.

STUDY 2

One apartment block set as control, another apartment block set as treatment

``` r
Nilsson_Control2 <- 301.1 - 290.9
282.4-287.8 - Nilsson_Control2 #Effect of treatment group using difference in difference
```

    ## [1] -15.6

``` r
15.6*12*min_int
```

    ## [1] 25.0848

``` r
15.6*12*max_int
```

    ## [1] 142.6464

``` r
15.6*12*avg_int
```

    ## [1] 85.176

The treatment group INCREASED electricity usage by 15.6KWh per month or 85.18kgCO2e/year or range of 25.08-142.65kgCO2e increase per year (NOT significant)

\*\*OZAWA ET AL. 2017 Tailored information/feedback is provided to households grouped according to three types of household energy consumption. One could frame the effect of this intervention as the effect of three unique interventions on three unique audiences or the effect of a single treatment consisting of three targeted interventions. We have chosen the latter. Additionally, the authors describe the presence of the boomerang effect, where households who are below average consumption levels increase consumption after finding out their relative standing, even though a normative encouragement is provided. The authors, report their results with this effect removed. We calculate the results both with and without the boomerang effect. Neither result is significant.

With boomerang effect: 0.067KWh/day increase (Table 3) Without boomerang effect: 0.382KWh/day decrease (Table 4)

``` r
0.067*365*min_int
```

    ## [1] 3.27697

``` r
0.067*365*max_int
```

    ## [1] 18.63471

``` r
0.067*365*avg_int
```

    ## [1] 11.12703

``` r
0.382*365*min_int
```

    ## [1] 18.68362

``` r
0.382*365*max_int
```

    ## [1] 106.2457

``` r
0.382*365*avg_int
```

    ## [1] 63.44065

This intervention can INCREASE emissions by 11.13kgCO2e/year or range of 3.27-18.63kgCO2e/year if messages are sent to all consumers. Tailored intervention can decrease emissions by 63.44kgCO2e/year or range from 18.68-106.25kgCO2e/year if messages are not sent to households who consume below average levels of electricity.

\*\*PETERSEN ET AL. 2007

18 dormitories with 1743 (see calculations) individuals are placed in a competition, provided with feedback and given instructions for reducing energy use. Treatment period compared to baseline period during which weather conditions were similar. Overall 68300kWh were saved over two weeks.

``` r
5368/3.08 #Calculate number of participants using their per capita cost calculations on page 12 
```

    ## [1] 1742.857

``` r
68300/1743/2*52*min_int #Find emissions per student per year
```

    ## [1] 136.5216

``` r
68300/1743/2*52*max_int
```

    ## [1] 776.3394

``` r
68300/1743/2*52*avg_int
```

    ## [1] 463.5622

Emissions saved are therefore estimated at 464kgCO2e with a range of 137-776kgCO2e/student per year

\*\*SCHLEICH ET AL. 2013

The treatment group was offered either online or mailed paper feedback. Although the groups are randomized the researchers make use of a regression model to account for differences between the control and treatment group such as household size, and they report an annual decrease of 154KWh in the treatment group (p&lt;0.05).

``` r
154*min_int
```

    ## [1] 20.636

``` r
154*max_int
```

    ## [1] 117.348

``` r
154*avg_int
```

    ## [1] 70.07

The treatment reduces emissions by 70kgCO2e/year or range of 21-117kgCO2e per year.

SCHULTZ ET AL. 2015 Three treatments are compared to a control: Feedback on energy use, feedback on energy use and cost, and feedback with a normative frame. Values are not provided in kWh for the three month mark, so we are not able to take the longest timeline. Statistics are provided for the one week value so we make use of that.

``` r
Schultz_cont <- 24.07-21.65 #Subtract week one from baseline

FeedbackIHD <- 23-21.37 
CostIHD <- 26.02-23.15
NormIHD <- 22.3-22.13
FeedbackIHD -Schultz_cont
```

    ## [1] -0.79

``` r
CostIHD - Schultz_cont
```

    ## [1] 0.45

``` r
NormIHD - Schultz_cont
```

    ## [1] -2.25

``` r
(FeedbackIHD -Schultz_cont) *365*min_int
```

    ## [1] -38.6389

``` r
(FeedbackIHD -Schultz_cont) *365*max_int
```

    ## [1] -219.7227

``` r
(FeedbackIHD -Schultz_cont) *365*avg_int
```

    ## [1] -131.1993

``` r
(CostIHD - Schultz_cont) *365*min_int
```

    ## [1] 22.0095

``` r
(CostIHD - Schultz_cont) *365*max_int
```

    ## [1] 125.1585

``` r
(CostIHD - Schultz_cont) *365*avg_int
```

    ## [1] 74.73375

``` r
(NormIHD - Schultz_cont) *365*min_int
```

    ## [1] -110.0475

``` r
(NormIHD - Schultz_cont) *365*max_int
```

    ## [1] -625.7925

``` r
(NormIHD - Schultz_cont) *365*avg_int
```

    ## [1] -373.6687

The feedback treatment decreased consumption by 0.79KWh/day (not significant) or 131.2kgCO2e/year with a range of 38.6-219.7kgCO2e per year The cost treatment INCREASED consumption by 0.45KWh/day (not significant) or 74.7kgCO2e with a range of 22.0-125.2kgCO2e per year The norm treatment decreased consumption by 2.25KWh/day (p&lt;0.05) or 373.7kgCO2e/year with a range of 110.0-625.8kgCO2e

\*\*SCHULTZ ET AL. 2007

Peer comparison feedback is compared to peer comparison feedback with a normative injunctive message (smiley face). There is no proper control group with no intervention. All groups received tips on how to conserve energy and feedback. Additionally, the authors do not report significance between the two treatments, but between the baseline and the treatment period. This is problematic for our purposes as they do not account for changes in weather during the two periods. We make use of the difference between the full treatment and the partial treatment (as if partial treatment was a control) which is the most conservative method and will result in underestimations of the effect, but allows for control of the weather. Because the longer term change in usage was "calculated by subtracting the meter reading taken the day of the second message from the final meter reading" instead of using the original baseline, we rely only on the short term change.

They break the full and partial treatments into two groups each, those who consume above the mean (high) and those who consume below the mean (low).

``` r
Norm_only_high <- 21.47-20.25 #Baseline subtract treatment
Norm_only_low <- 10.38-11.27 #Baseline subtract treatment

full_high <- 20.63-18.91 - Norm_only_high
full_low <- 10.34-10.58 - Norm_only_low

full_high*52*max_int
```

    ## [1] 19.812

``` r
full_high*52*min_int
```

    ## [1] 3.484

``` r
full_high*52*avg_int
```

    ## [1] 11.83

``` r
full_low*52*max_int
```

    ## [1] 25.7556

``` r
full_low*52*min_int
```

    ## [1] 4.5292

``` r
full_low*52*avg_int
```

    ## [1] 15.379

The full treatment resulted in 0.5KWh reductions over one week in the high users compared to the partial treatment or 11.8kgCo2e/year with a range of 3.5-19.8kgCO2e/year The full treatment resulted in 0.65KWh reductions over one week in the low users compared to the partial treatment or 15.4kgCO2e/year or range of 4.5-25.8kgCO2e/year

Interpret with caution as this second group still had an overall increase in consumption compared to their baseline and there is no proper control.

\*\*SENBEL ET AL. 2014

Feedback and competition used to decrease residential energy use at university residences. 1757 students were eligible to join the treatment group, we therefore divide total energy savings by this number (to find the intent to treat effect). Reductions per day for this group were found to be 232.99kWh/day (significant at p&lt;0.01)

``` r
232.99/1757 #Find energy savings per day per student
```

    ## [1] 0.1326067

``` r
(232.99/1757)*365*min_int
```

    ## [1] 6.485794

``` r
(232.99/1757)*365*max_int
```

    ## [1] 36.88191

``` r
(232.99/1757)*365*avg_int
```

    ## [1] 22.02266

The treatment therefore reduced energy use by 0.13KWh/day per student or 22.02kgCO2e/year with a range of 6.49-36.88kgCO2e per year per student.

\*\*SINTOV ET AL. 2016

The group competition reportedly reduced consumption in the 39 suites by 3158KWh over the three week intervention period (p&lt;0.01)

``` r
3158/3/39 #Divide by three weeks and by number of suites
```

    ## [1] 26.99145

``` r
(3158/3/39)*52*min_int #Find emissions per year
```

    ## [1] 188.0764

``` r
(3158/3/39)*52*max_int
```

    ## [1] 1069.509

``` r
(3158/3/39)*52*avg_int
```

    ## [1] 638.6178

The intervention reduced energy usage by 26.99KWh/suite/week or 639kgCO2e or range from 188-1070kgCO2e per year (significant)

\*\*SUDARSHAN 2017

"Inform\_Only" treatment group (n=119) received instructions and peer feedback and reduced energy by 3530.93KWh over 120 days (p&lt;0.1) while "Inform\_Incent" (n=233) received instructions, peer feedback and rewards but increased energy usage (710.83) over the same time.

``` r
Inform_Only<- 3530.93/119/120 #Find kWh saved per household per day
Inform_Only*365*min_int #Find emissions per year
```

    ## [1] 12.09368

``` r
Inform_Only*365*max_int
```

    ## [1] 68.77154

``` r
Inform_Only*365*avg_int
```

    ## [1] 41.06437

``` r
Inform_Incent<- 710.83/233/120 #Find KWh saved per house per day
Inform_Incent
```

    ## [1] 0.0254231

``` r
Inform_Incent*365*min_int
```

    ## [1] 1.243444

``` r
Inform_Incent*365*max_int
```

    ## [1] 7.070928

``` r
Inform_Incent*365*avg_int
```

    ## [1] 4.222142

The information only treatment group reduced energy use by 0.25KWh/day/household or 41.06kgCO2e/year with range of 12.09-68.77KgCO2e/year (p&lt;0.1)

The information and incentive group INCREASES energy use by 0.03KWh/day and emissions by 4.22kgCO2e/year with range of 1.24-7.07kgCO2e/year

\*\*SUTER & SHAMMIN 2013

The authors report results after the first year using an econometric model. However the sample size for some treatments (three households in the treatment group Incentive+Thermo) is quite small, so we utilize only their pairwise comparison chart (Table 1) where n=24 and results are totalled over one year. These results are more conservative, no changes are significant relative to the control, whereas in the econometric model some changes are significant. We exclude the installation of attic insulation as no choice was given to the residents so this is purely a structural intervention.

Control decreases natural gas by 0.64ccf/day Thermostat decreases natural gas by 0.06ccf/day Incentive decreases natural gas by 1.07ccf/day

53.12kgCO2e/Mcf (thousand cubic feet) or 5.312kgCO2/ccf <https://www.eia.gov/environment/emissions/co2_vol_mass.php>

``` r
#Thermostat
0.06-0.64 #Effect of thermostat compared to control
```

    ## [1] -0.58

``` r
0.58*365*5.312 #Find emissions per year
```

    ## [1] 1124.55

``` r
#Incentive
1.07-0.64
```

    ## [1] 0.43

``` r
0.43*365*5.312
```

    ## [1] 833.7184

The thermostat treatment INCREASES energy use by 0.58ccf/day or 1124.55kgCO2 per year (not significant) The incentive treatment decreases energy use by 0.43ccf/day or 833.72kgCO2 per year (not significant)

\*\*THONDHLANA & KUA 2016

Two treatment groups for low income households: Full treatment (FT = pamphlets, feedback, personal instructions) and Partial Treatment (PT = pamphlets only). We use the difference between August and April for the following calculation (Table 3). Numbers are reported per capita but to make them comparable to other studies whose unit of analysis is the household, we multiply by the average household size of the full sample (four).

Control: Decreased usage by 4.81KWh/month PT: Decreased usage by 9.98KWh/month FT: Decreased usage by 24.50KWh/month

``` r
Thondhlana_control <- 4.81

#Partial treatment
(9.98- Thondhlana_control)
```

    ## [1] 5.17

``` r
(9.98- Thondhlana_control)*12*4*min_int #Find emissions per year per household
```

    ## [1] 33.25344

``` r
(9.98- Thondhlana_control)*12*4*max_int
```

    ## [1] 189.0979

``` r
(9.98- Thondhlana_control)*12*4*avg_int
```

    ## [1] 112.9128

``` r
#Full treatment
(24.50 - Thondhlana_control)
```

    ## [1] 19.69

``` r
(24.50 - Thondhlana_control)*12*4*min_int
```

    ## [1] 126.6461

``` r
(24.50 - Thondhlana_control)*12*4*max_int
```

    ## [1] 720.1814

``` r
(24.50 - Thondhlana_control)*12*4*avg_int
```

    ## [1] 430.0296

The partial treatment decreased usage by 5.17KWh/month per capita or 112.92KgCO2e/year with a range of 33.25-189.10kgCO2e/year (not significant) compared to the control The full treatment decreased usage by 19.69KWh/month per capita or 430.03kgCO2e/year with range of 126.65-720.18kgCO2e/year per household (significant P=0.000) compared to the control

\*\*WILHITE & LING 1995 The first treatment group received more frequent feedback, second group received more frequent feedback and their historical usage, and group three received frequent feedback, historical usage and energy saving tips. The three treatment groups all reduced energy use, but were not significantly different from one another and the authors lump them into one group for calculations.

Annual reductions of 1348kWh in the final year.

``` r
1348*min_int
```

    ## [1] 180.632

``` r
1348*max_int
```

    ## [1] 1027.176

``` r
1348*avg_int
```

    ## [1] 613.34

Emissions reductions estimated at 613kgCO2e/year with a range of 181-1027kgCO2e/year

\*\*WILLIS ET AL. 2010

A shower alarm (which goes off after 40L of water has been used) was installed to reduce water consumption. The researchers measures changes in water consumption, but use these changes to estimate energy saved and suggest 602KWh per household are saved annually.

``` r
602*min_int
```

    ## [1] 80.668

``` r
602*max_int
```

    ## [1] 458.724

``` r
602*avg_int
```

    ## [1] 273.91

The treatment group reduces emissions by 274kgCO2e/year or range of 81-459kgCO2e/year. Reductions in water usage were significant (p&lt;0.0005 for shower volume reductions)

\*\*XU ET AL. 2015

The treatment group has IHD devices present in the house and the control group does not. No mention of significance or randomization and we assume a quasi-experimental setup.

Treament group (with IHD): 91.0kWH per month Control group (without IHD): 100.1kWh per month

``` r
100.1-91.0 #Find energy saved per month
```

    ## [1] 9.1

``` r
(100.1-91.0)*12*min_int   # Find emissions saved per year
```

    ## [1] 14.6328

``` r
(100.1-91.0)*12*max_int 
```

    ## [1] 83.2104

``` r
(100.1-91.0)*12*avg_int
```

    ## [1] 49.686

Presence of the IHD results in 9.1kWh reductions per month per apartment or 49.7kgCO2e with a range of 14.6-83.2kgCO2e saved per year (not significant)
