STAT 545A Homework 2
================
Tian Gao
2018/9/20

# Bring rectangular data in

``` r
library(tidyverse)
```

    ## -- Attaching packages --------------------------------------------------- tidyverse 1.2.1 --

    ## √ ggplot2 3.0.0     √ purrr   0.2.5
    ## √ tibble  1.4.2     √ dplyr   0.7.6
    ## √ tidyr   0.8.1     √ stringr 1.3.1
    ## √ readr   1.1.1     √ forcats 0.3.0

    ## -- Conflicts ------------------------------------------------------ tidyverse_conflicts() --
    ## x dplyr::filter() masks stats::filter()
    ## x dplyr::lag()    masks stats::lag()

``` r
library(gapminder)
```

# Smell test the data

## Is it a data frame, a matrix, a vector, a list?

``` r
class(gapminder)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

  - This is a data frame

## what is its class?

  - Its classes are tbl\_df, tbl,
data.frame

## How many variables/columns?

``` r
ncol(gapminder)
```

    ## [1] 6

## How many rows/observations?

``` r
nrow(gapminder)
```

    ## [1] 1704

## Can you get these facts about “extent” or “size” in more than one way? Can you imagine different functions being useful in different contexts?

``` r
dim(gapminder)
```

    ## [1] 1704    6

## What data type is each variable?

``` r
str(gapminder)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1704 obs. of  6 variables:
    ##  $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
    ##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
    ##  $ gdpPercap: num  779 821 853 836 740 ...

  - We can see that there are six variables:
  - “country” is Factor
  - “continent” is Factor
  - “year” is int
  - “lifeExp” is num
  - “pop” is int
  - “gdpPercap” is num

# Explore individual variables

## What are possible values of each variables?

``` r
unique(gapminder$year)
```

    ##  [1] 1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 2002 2007

``` r
range(gapminder$year)
```

    ## [1] 1952 2007

  - Above are the unique values and range of “year” variable

<!-- end list -->

``` r
unique(gapminder$continent)
```

    ## [1] Asia     Europe   Africa   Americas Oceania 
    ## Levels: Africa Americas Asia Europe Oceania

  - Above are the unique values of “year” variable.

## What values are typical? What’s the spread? What’s the distribution?

``` r
frequency_year = table(gapminder$year)
frequency_continent = table(gapminder$continent)
frequency_year
```

    ## 
    ## 1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 2002 2007 
    ##  142  142  142  142  142  142  142  142  142  142  142  142

``` r
frequency_continent
```

    ## 
    ##   Africa Americas     Asia   Europe  Oceania 
    ##      624      300      396      360       24

  - We can see that, from the aspect of year, the sample is equally
    distributed, every year appeard 142 times
  - From the aspect of continent, the typical value is “Africa”

<!-- end list -->

``` r
summary(gapminder$year)
```

    ##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
    ##    1952    1966    1980    1980    1993    2007

``` r
summary(gapminder$continent)
```

    ##   Africa Americas     Asia   Europe  Oceania 
    ##      624      300      396      360       24

# Explore various plot types

## Make a few plots, probably of the same variable you chose to characterize numerically. You can use the plot types we went over in class (cm006) to get an idea of what you’d like to make. Try to explore more than one plot type. Just as an example of what I mean:

# A scatterplot of two quantitative variables.

# A plot of one quantitative variable. Maybe a histogram or densityplot or frequency polygon.

# A plot of one quantitative variable and one categorical. Maybe boxplots for several continents or countries.

# You don’t have to use all the data in every plot\! It’s fine to filter down to one country or small handful of countries.
