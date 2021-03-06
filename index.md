---
title       : Red Wine Quality Predictor
subtitle    : Professionaly determine the quality of your red wine with analyzing ingredients
author      : Farshid Mahdavipour
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---



## Wine Making Competition
This is always a professional task to taste wine and 
give feedbacks to winemakers. 
Many factors are included ine the ratings, but it is a good idea for winerys
to have a prediction on their wine quality before participating in competitions! 

#### Wine Quality Dataset
There is a wine quality dataset, developed from the north of Portugal. The goal is to model wine quality based on physicochemical tests.
you can download the original dataset from the UCI Machine Learning Database.
https://archive.ics.uci.edu/ml/datasets/Wine+Quality

--- .class #id 
## Downloading Dataset
First of all, we will download the dataset, create the dataframe and running correlations between the all wine features, three characteristics has been selected for the prediction formula

```r
winedata <- read.csv("http://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-red.csv",sep=";")
cor(winedata)
```
P. Cortez, A. Cerdeira, F. Almeida, T. Matos and J. Reis. 
Modeling wine preferences by data mining from physicochemical properties. In Decision Support Systems, Elsevier, 47(4):547-553, 2009.

--- .class #id 
## Prediction Algorithm
The predicting function is a simple linear regression based on the Alcohol content, vlatile acidity and residual sugar. 

```r
fit <- lm(quality~alcohol+volatile.acidity+residual.sugar,data=winedata)
print(fit$coef)
```

```
##      (Intercept)          alcohol volatile.acidity   residual.sugar 
##      3.098825118      0.313916847     -1.383483209     -0.001781068
```
so we come up with this formula for the prediction:

winequality <- 0.313917 * alcohol-1.383483 * volatile.acidity-0.001781 * residual.sugar 

--- .class #id
## The web application
The web application is deployed to shiny servers at this location:
http://farchide.shinyapps.io/shiny

<img src="http://www.statestreetwineryredlands.com/webftp/u14/pictures/glass-of-red-wine.jpg" />

You can play around and check the quality of your home made wine professionaly!





