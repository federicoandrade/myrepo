Chapter6
================
Federico Andrade-Rivas
January 23, 2020

Pipe operator
-------------

It has a short cut that is CTRL +Shift +M It takes what its to the left of the pipe and applies the functions to the right. You can see the pipe operator as a "gets" or "then".

``` r
library(tidyverse)
```

    ## ── Attaching packages ────────────────────────────────────────────────────────────────────────────────────── tidyverse 1.3.0 ──

    ## ✔ ggplot2 3.2.1     ✔ purrr   0.3.3
    ## ✔ tibble  2.1.3     ✔ dplyr   0.8.3
    ## ✔ tidyr   1.0.0     ✔ stringr 1.4.0
    ## ✔ readr   1.3.1     ✔ forcats 0.4.0

    ## ── Conflicts ───────────────────────────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
library(gapminder)
gapminder %>% head()
```

    ## # A tibble: 6 x 6
    ##   country     continent  year lifeExp      pop gdpPercap
    ##   <fct>       <fct>     <int>   <dbl>    <int>     <dbl>
    ## 1 Afghanistan Asia       1952    28.8  8425333      779.
    ## 2 Afghanistan Asia       1957    30.3  9240934      821.
    ## 3 Afghanistan Asia       1962    32.0 10267083      853.
    ## 4 Afghanistan Asia       1967    34.0 11537966      836.
    ## 5 Afghanistan Asia       1972    36.1 13079460      740.
    ## 6 Afghanistan Asia       1977    38.4 14880372      786.

Using select
------------

Back do dplyr

``` r
select(gapminder, year, lifeExp)
```

    ## # A tibble: 1,704 x 2
    ##     year lifeExp
    ##    <int>   <dbl>
    ##  1  1952    28.8
    ##  2  1957    30.3
    ##  3  1962    32.0
    ##  4  1967    34.0
    ##  5  1972    36.1
    ##  6  1977    38.4
    ##  7  1982    39.9
    ##  8  1987    40.8
    ##  9  1992    41.7
    ## 10  1997    41.8
    ## # … with 1,694 more rows

Same operation but written with pipe. Also, two ways of getting to the ssame result with typical R and pipes

``` r
gapminder %>% 
  select(year, lifeExp) %>% 
  head(4)
```

    ## # A tibble: 4 x 2
    ##    year lifeExp
    ##   <int>   <dbl>
    ## 1  1952    28.8
    ## 2  1957    30.3
    ## 3  1962    32.0
    ## 4  1967    34.0

``` r
gapminder[gapminder$country == "Cambodia", c("country", "year")]
```

    ## # A tibble: 12 x 2
    ##    country   year
    ##    <fct>    <int>
    ##  1 Cambodia  1952
    ##  2 Cambodia  1957
    ##  3 Cambodia  1962
    ##  4 Cambodia  1967
    ##  5 Cambodia  1972
    ##  6 Cambodia  1977
    ##  7 Cambodia  1982
    ##  8 Cambodia  1987
    ##  9 Cambodia  1992
    ## 10 Cambodia  1997
    ## 11 Cambodia  2002
    ## 12 Cambodia  2007

``` r
gapminder %>% filter(country=="Cambodia") %>% select(year, lifeExp)
```

    ## # A tibble: 12 x 2
    ##     year lifeExp
    ##    <int>   <dbl>
    ##  1  1952    39.4
    ##  2  1957    41.4
    ##  3  1962    43.4
    ##  4  1967    45.4
    ##  5  1972    40.3
    ##  6  1977    31.2
    ##  7  1982    51.0
    ##  8  1987    53.9
    ##  9  1992    55.8
    ## 10  1997    56.5
    ## 11  2002    56.8
    ## 12  2007    59.7
