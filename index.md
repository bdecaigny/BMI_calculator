---
title       : BMI Calculator
subtitle    : for Coursera course 'Developing Data Products'
author      : Bart Decaigny
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Background

# Obesitas
One of the growing risks to population health - especially, but not exclusively
in developed countries - is overweight. This is roughly caused by too much and
too rich food (or toherwise unbalanced diet), lack of exercises etc .  
The weight problem is often shorthanded as obesitas, for using a more neutral
term. One of the quick checks one can do to asses the risk for obesitas, is 
calculating the body mass index or BMI - a relation between weight and length.
The medical interpretation on this index is not always anonymous (see a.o. 
Wikipedia -e.g. using waist circumference proves to be a better predictor for 
the risk on cardiovascular problems), but it is a useful tool for raising
awareness.

--- .class #id 

## BMI calculation & rangess

The Index is simply calculated by dividing a person's weight (in kg), by the 
square of his/her heigth (in m). This should give a number roughly between 10
and 50. This calculated index is then compared to ranges for assessing the health
of the person regarding his weight. Note that several (slightly different) ranges
can be found, sometimes for simplification, sometimes for catering for racial 
differences. Note also that no ranges are used for children under 20 years, the 
BMI is for them instead compared to percentiles. A common found set of BMI ranges
loooks like this:

- < 18.5: Underweight
- between 18.5 and 25: normal (healthy) weight
- between 25 and 30: overweight
- between 30 and 35: obese
- over 35: morbidly obese

--- .class #id 

## Calculation of BMI in the demo application

The demo application requests your weight (default: 75 kg) and height (default:
175 cm), and an optional target BMI (default: 23.5). This input is then used to
calculate your BMI, and how much kg you should lose (or gain) to reach your target.

The calculation for the BMI is like this:

```r
weight <- 75
height <- 175

weight/(height*height/10000) ## since height is given in cm, but should be in m
```

```
## [1] 24.49
```

--- .class #id 

## Calculation of the target weight in the demo application

For the target this becomes:

```r
weight <- 75
height <- 175

target <- 23.5

round(((target - (weight/(height*height/10000)))*(height*height/10000)), digits = 2)
```

```
## [1] -3.03
```
Based on the result of this calculation, the web page gives some encouragement message...

