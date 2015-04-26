--- 
title       : User-Friendly Application for MPH Prediction 
subtitle    : Based on mtcars dataset
author      : Eotoke
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
--- 

## Problem
 
To predict a value like mph for cars, users often have to go through multiple ways like manual computation or learn R programming. Without a common and shared application, users might also spend additional time and effort repeating their computations.

As such, this potentially will cause problems like 
- errors
- frustration
- wastage of manpower, time, effort

--- .class #id

## Proposed Solution

In order to hide the complexities of programming and make prediction repeatable and easy, a Shiny application is developed with user friendly inputs. 

Users will only need to adjust the values and their inputs and prediction result is presented in a easy to read table form i.e.

Inputs:

```
##    hp wt cyl am
## 1 110  3   4  1
```

Results:

```
##    mph
## 1 22.5
```

--- .class #id

## Key Benefits of the Application

1. Easy to use User Interface for adjusting of values
2. Repeatable Prediction without manual coding or computation
3. Sharable Application
4. Easy Update of data source and algorithm

Overall, this saves time, effort and maintenance from users and reduces error due to manual computation.

--- .class #id

##  Design behind the application

Using the mtcars dataset,

- Regression is based on regressing mpg with horsepower (hp), weight (wt), transmission (am) and number of cylinders (cyl).


```r
library(datasets)
data(mtcars)
fit<-lm(mpg ~ hp + wt + factor(am) + factor(cyl), data=mtcars)
```

- Consolidating the values reactively based on user inputs, the predict function is used to predict the mph.


```r
predict(fit,
        data.frame("hp"=input$horsepower,"wt"=input$weight,
                   "cyl"=input$cylinder,"am"=input$am)
```

