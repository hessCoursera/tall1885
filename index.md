---
title       : Coursera Project on Developing Data Products
subtitle    : App   -    Would you be tall in 1885
author      : 
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Question: Would you be tall in 1885?

Creating an app that should:

1. Read in user height

2. Load the Galton dataset

3. Compute the Percentage of men in 1885 that are shorter


--- .class #id 

## Read in user height
Input via a slider which let user choose his height

```r
sliderInput('myheight', 'What is your height (inches)'
            ,value = 72, min = 60, max = 85, step = 0.05,)
```

and display its location on the distribution:

```r
  hist(galton$child, xlab='height', col='lightblue',main='Probability', prob=TRUE)
  curve(dnorm(x,mean=mean(galton$child),sd=sd(galton$child)),add=TRUE)
```


--- .class #id 

## Compute the Probability:
Get the mean and standard deviation of the galton data

```r
library(UsingR)
data(galton)
c(mean(galton$child),sd(galton$child))
```

```
## [1] 68.088470  2.517941
```

Compute the probability of a man of 1885 who's shorter:
Example for 70 inches

```r
height=70
pnorm(height,mean=mean(galton$child),sd=sd(galton$child))
```

```
## [1] 0.7761227
```

--- .class #id 

## Summary
Created an app that:
  * reads user height
  * computes continuos PDF from the galton data
  * computes the probability of a man of 1885 being shorter
  * is available at: https://hesscoursera.shinyapps.io/project/

