Personal Vehicle Calculations
================
Seth Wynes
June 6, 2018

For all vehicles we take 260gCO2e/km as the life cycle emissions associated with an internal combustion vehicle, and for a lower range 180gCO2e/km as the life cycle emissions associated with an electric vehicle, using the European electrical mix rather than assuming coal or natural gas to ensure that this provided a lower range estimate (Hawkins et al. 2013, SI - corrigendum version)

``` r
ICV <- 0.260
EV <- 0.180
```

\*\*JAKOBSSON ET AL. 2002

We take weekly driving distance in the After Treatment category and subtract the Before treatment driving distance for control.

``` r
#Control
377-321
```

    ## [1] 56

Control increases driving 56km

Now repeat for all categories, subtracting the distance of the control group.

``` r
Charge <- 285-306-56
Charge
```

    ## [1] -77

``` r
Charge*ICV*52
```

    ## [1] -1041.04

``` r
Charge*EV*52
```

    ## [1] -720.72

``` r
Charge_plan <-271-291-56
Charge_plan*ICV*52
```

    ## [1] -1027.52

``` r
Charge_plan*EV*52
```

    ## [1] -711.36

``` r
Ext_charge_plan <- 303-311-56
Ext_charge_plan*ICV*52
```

    ## [1] -865.28

``` r
Ext_charge_plan*EV*52
```

    ## [1] -599.04

Charge: 77 km reduced per week (1041kgCO2e reduced per year or 721 in an EV)

Charge and plan: 76km reduced per week (1027kgCO2e/year or 711 in an EV)

Extended charge and plan: 64km reduced per week (17kgCO2e/week or 865kgCO2e/year or 599 in an EV)

"no signicant within-subjects effects could be found. None of the instruments caused a decrease in car use"

\*\*MOKHTARIAN & VARMA 1998 NOTE: Excluded from results as this is a structural intervention. Telecenters are made available and used roughly once per work week (1.25/5) by the treatment group generating a reduction in total VMT of 35.2 on those days.

``` r
35.2*1.609*1.25*48*ICV #Convert to km, multiply by times used per week and assume a 48 week work year
```

    ## [1] 883.5341

``` r
35.2*1.609*1.25*48*EV #Emissions for an electric vehicle
```

    ## [1] 611.6774

This would reduce emissions by 883.5kgCO2e/year in an ICV or 611.7kgCO2e/year in an EV. Not significant.The authors state, "A reasonable inference from the evidence to date is that the data are exhibitng random fluctuations around an average of no change".

\*\*PENDYALA ET AL. 1991 Travel diaries are used to compute reductions in distance travelled for a treatment group that telecomuted compared to control groups which did not. With the format of reported results it is difficult to know how to compute a difference in difference result and so we instead use a pre-post difference as this is how the authors report the change in the text. This amounts to a 40.5miles/day reduction (p&lt;0.05 reported).

We assume one day of teleconferencing per week and a 48 week work year.

``` r
40.5*1.609*48*ICV #Convert to km and find annual emissions in an ICV
```

    ## [1] 813.253

``` r
40.5*1.609*48*EV #Annual emissions in an EV
```

    ## [1] 563.0213

This intervention would be expected to reduce emissions by 813.3kgCO2e/year for an ICV and 563.0kgCo2e in an EV

\*\*RUFOLO & KIMPEL 2008 Intervention group charged per vmt (VMT), Peak hour group charged high VMT fee during peak hours, but lower fee at other times (PH), and Control group (Control). Both the PH group and the VMT group had "significant" changes, but only in respect to their own baseline, not in respect to the control group.

``` r
#Control decreases 0.994 miles per day
#VMT decreases 2.856 miles per day
#PH decreases 5.102 miles per day

VMT <- 1.609*(2.856-0.994) #Subtract control and convert to km
PH <- 1.609*(5.102-0.994)
VMT*365*ICV
```

    ## [1] 284.3164

``` r
VMT*365*EV
```

    ## [1] 196.8344

``` r
PH*365*ICV
```

    ## [1] 627.2674

``` r
PH*365*EV
```

    ## [1] 434.262

``` r
Control<-0.994*1.609*7 #To find km per week of control group
Control
```

    ## [1] 11.19542

VMT intervention reduces kilometers travelled per day by 2.996 or 20.97km/week (284.32kgCO2e/year or 196.83 in an EV)

PH intervention reduces kilometers travelled per day by 6.609 or 46.27km/week (627.27kgCO2e/year or 434.26 in an EV)

\*\*SHOUP 1997 Eight firms give option of cashing out parking spaces to employees. Measured increased reports of car-pooling, change in vkt. Although each firm provided slightly different compensation packages (the cost of parking was different at each firm, some firms also offered subsidies for public transit etc.) the authors treat the results as one unit, averaging out vkt and CO2 reductios, so we do likewise.

``` r
#They claim 367kgCO2 is saved per employee per year
367/52
```

    ## [1] 7.057692

``` r
#They also claim 1050vkt reduced per employee per year
1050*ICV
```

    ## [1] 273

``` r
1050*EV
```

    ## [1] 189

By our calculations, emissions would decrease 273kgCO2e/year (or 189 in EV)

\*\*TERTOOLEN 1998 Information and feedback about the environmental effects of cars given to treatment (E), the cost of cars (CC), both (EC) and no information or feedback given to (N). All groups were provided with information on local public transit and self-monitored. A control (CC) was present but results in km were not provided for the control. Therefore we have chosen to subtract the no-information category (N) to act as control. No results were significant.

``` r
E <- 401-359 #Increase in driving 
C <- 427-367 #Increase in driving
EC <- 396-410 #Decrease in driving
N <- 425-357 #Increase in driving
N
```

    ## [1] 68

``` r
E-N #Decrease of 26km over 2 weeks compared to N
```

    ## [1] -26

``` r
C-N #Decrease of 8km over 2 weeks compared to N
```

    ## [1] -8

``` r
EC-N #Decrease of 82km over 2 weeks compared to N
```

    ## [1] -82

``` r
(E-N)/2*52*ICV #Find annual emissions
```

    ## [1] -175.76

``` r
(E-N)/2*52*EV 
```

    ## [1] -121.68

``` r
(C-N)/2*52*ICV
```

    ## [1] -54.08

``` r
(C-N)/2*52*EV
```

    ## [1] -37.44

``` r
(EC-N)/2*52*ICV 
```

    ## [1] -554.32

``` r
(EC-N)/2*52*EV 
```

    ## [1] -383.76

Environmental feedback reduced km driven by 42km over two weeks (compared to no feedback) or 176kgCO2e/year (122 in EV) (not significant) Cost feedback reduced km driven by 8km over two weeks or 54kgCO2e/year (37 in EV) (not significant) Environmental and cost feedback reduced km driven by 82km over two weeks or 554kgCO2e/year (384 in EV) (not significant)
