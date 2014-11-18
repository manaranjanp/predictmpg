---
title       : Predicting a Car's Mileage
subtitle    : How much miles per gallon?
author      : Manaranjan Pradhan
job         : Data Enthusiast
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## What does this app do?

1. Predicting car's efficiency
2. How many miles per gallon the car runs?
3. This can be predicted from car's Weight, Transmission type and hp
4. Uses historical data to build a regression model to learn and predict

__A note for car buyer: Know car's efficiency before deciding to buy__

--- .class #id 

## Using historical data to build a model

Using _mtcars_ data and only wt, hp and am columns


```r
head( mtcars[ ,c( "mpg", "wt", "hp", "am")] )
```

```
##                    mpg    wt  hp        am
## Mazda RX4         21.0 2.620 110    Manual
## Mazda RX4 Wag     21.0 2.875 110    Manual
## Datsun 710        22.8 2.320  93    Manual
## Hornet 4 Drive    21.4 3.215 110 Automatic
## Hornet Sportabout 18.7 3.440 175 Automatic
## Valiant           18.1 3.460 105 Automatic
```

--- .class #id 

## Exploring relationships 

![plot of chunk unnamed-chunk-2](assets/fig/unnamed-chunk-2.png) 

From the plots, mpg seems to be negatively correlated with wt and hp. Also, manual transmission have higher mpg compared to automatic transmission types. 

--- .class #id 

## Building the regression model 


```r
fit1 <- lm( mpg ~ wt + hp + am, data = mtcars )
summary( fit1 )$coefficients
```

```
##             Estimate Std. Error t value  Pr(>|t|)
## (Intercept) 34.00288   2.642659  12.867 2.824e-13
## wt          -2.87858   0.904971  -3.181 3.574e-03
## hp          -0.03748   0.009605  -3.902 5.464e-04
## amManual     2.08371   1.376420   1.514 1.413e-01
```
__Notes:__

From p-values, it is apparent that all the predictors are significant.

Adjdusted r square value indicates that the equation can explain ``82.2736``% of the total variations in the mpg for different cars.

--- .class #id 

## Using the app to predict miles per gallon

Access the application using the url 
[http://manaranjanp.shinyapps.io/predictmpg](http://manaranjanp.shinyapps.io/predictmpg)

![width](app.png)
