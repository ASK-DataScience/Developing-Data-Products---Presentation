---
title       : Predicting MPG 
subtitle    : Prediction of MPG (Miles/(US) gallon) for different cars
author      : ASK-DataScience
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Introduction

Here, we are trying to predict the MPG (Miles/(US) gallon) for differenct cars using:
  
  
1. Transmission type (0 = Automatic, 1 = Manual)
2. Number of cylinders (4, 6, or 8)
3. Gross horsepower
4. Weight (lb/1000)

--- .class #id 

## Dataset

- mtcars data set was used in this analysis.


```r
data(mtcars)
head(mtcars)
```

```
##                    mpg cyl disp  hp drat    wt  qsec vs am gear carb
## Mazda RX4         21.0   6  160 110 3.90 2.620 16.46  0  1    4    4
## Mazda RX4 Wag     21.0   6  160 110 3.90 2.875 17.02  0  1    4    4
## Datsun 710        22.8   4  108  93 3.85 2.320 18.61  1  1    4    1
## Hornet 4 Drive    21.4   6  258 110 3.08 3.215 19.44  1  0    3    1
## Hornet Sportabout 18.7   8  360 175 3.15 3.440 17.02  0  0    3    2
## Valiant           18.1   6  225 105 2.76 3.460 20.22  1  0    3    1
```

```r
mtcars$am <- factor(mtcars$am)
```

--- .class #id 

## Regression Model

- Linear regression model was used. 
- The model includes the relationship between mpg (outcome) and transmission type, number of cylinders, gross horsepower. and weight (regressors).


```r
modelFit <- lm(mpg ~ am+cyl+hp+wt, mtcars)
modelFit
```

```
## 
## Call:
## lm(formula = mpg ~ am + cyl + hp + wt, data = mtcars)
## 
## Coefficients:
## (Intercept)          am1          cyl           hp           wt  
##      36.147        1.478       -0.745       -0.025       -2.606
```

--- .class #id 

## Prediction

- The user can enter his values for the regressors to get the predicted MPG value.
- This is done using the `predict` function.


```r
p <- predict(modelFit, newdata = test)
```










