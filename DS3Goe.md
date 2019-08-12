DS3Goe
================
Abigail Cochran
8/12/2019

First, I'll call the libraries that I may want to use for my analysis.

``` r
#Call necessary libraries
library(datasets)
library(ggplot2)
library(tidyverse)
```

    ## ── Attaching packages ─────────────────────────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ tibble  2.1.1     ✔ purrr   0.3.2
    ## ✔ tidyr   0.8.2     ✔ dplyr   0.8.0
    ## ✔ readr   1.3.1     ✔ stringr 1.4.0
    ## ✔ tibble  2.1.1     ✔ forcats 0.4.0

    ## ── Conflicts ────────────────────────────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

Then I'll download the data, and take a quick look.

``` r
#Call the IRIS dataset
data(iris)

#Summarize the dataset.
summary(iris)
```

    ##   Sepal.Length    Sepal.Width     Petal.Length    Petal.Width   
    ##  Min.   :4.300   Min.   :2.000   Min.   :1.000   Min.   :0.100  
    ##  1st Qu.:5.100   1st Qu.:2.800   1st Qu.:1.600   1st Qu.:0.300  
    ##  Median :5.800   Median :3.000   Median :4.350   Median :1.300  
    ##  Mean   :5.843   Mean   :3.057   Mean   :3.758   Mean   :1.199  
    ##  3rd Qu.:6.400   3rd Qu.:3.300   3rd Qu.:5.100   3rd Qu.:1.800  
    ##  Max.   :7.900   Max.   :4.400   Max.   :6.900   Max.   :2.500  
    ##        Species  
    ##  setosa    :50  
    ##  versicolor:50  
    ##  virginica :50  
    ##                 
    ##                 
    ## 

Great. Now let's figure something out. How about how the ratio of sepal length to width, and petal length to width differs across species. First, let's format the data as a dataframe.

``` r
#Make Iris into a dataframe.
dfiris <- as.data.frame(iris)

#Take a quick look at data types
str(dfiris)
```

    ## 'data.frame':    150 obs. of  5 variables:
    ##  $ Sepal.Length: num  5.1 4.9 4.7 4.6 5 5.4 4.6 5 4.4 4.9 ...
    ##  $ Sepal.Width : num  3.5 3 3.2 3.1 3.6 3.9 3.4 3.4 2.9 3.1 ...
    ##  $ Petal.Length: num  1.4 1.4 1.3 1.5 1.4 1.7 1.4 1.5 1.4 1.5 ...
    ##  $ Petal.Width : num  0.2 0.2 0.2 0.2 0.2 0.4 0.3 0.2 0.2 0.1 ...
    ##  $ Species     : Factor w/ 3 levels "setosa","versicolor",..: 1 1 1 1 1 1 1 1 1 1 ...

``` r
# All numerics and factors (for species), that's what we want.
```

Now let's manipulate the dataframe.

``` r
# First get the ratio for sepals and petals per line, then group by species, then get the average ratios for each species.

dfirismut <- dfiris %>%
  mutate(sepal.ratio = Sepal.Length/Sepal.Width) %>%
  mutate(petal.ratio = Petal.Length/Petal.Width) %>%
  group_by(Species) %>%
  mutate(sepal.lw.ratio.avg = mean(sepal.ratio)) %>%
  mutate(petal.lw.ratio.avg = mean(petal.ratio))
```

This worked. I get what I want. The average sepal length/width raio is 1.470188 for setosa, 2.160402 for versicolor, and 2.230453 for virginica. The average petal length/width ratio is 6.908 for setosa, 3.242837 for versicolor, and 2.780662 for virginica.

For sepals: virginica &gt; versicolor &gt; setosa.

For petals: setosa &gt; versicolor &gt; verginica.

This leads me to believe that these measurements might have an inverse relationsihp. Super!
