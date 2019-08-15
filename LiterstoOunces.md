LiterstoOunces
================
Abigail Cochran
8/15/2019

I am going to create a function that converts liters to ounces so that I know how much beer I've been drinking in Göttingen.

``` r
# Create my function, liters_to_ounces
liters_to_ounces <- function(vol_l) {
  vol_oz <- vol_l*33.814
  return(vol_oz)
}
```

I think my function, liters\_to\_ounces, should work. Let's test it out, to figure out how much Paulaner Hefeweizen I've consumed in Wilhelmsplatz.

``` r
# I usually have a half liter bottle, so 0.5 l. 
liters_to_ounces(0.5)
```

    ## [1] 16.907

Ok, so per beer I'm drinking 16.9 fluid ounces. I usually measure my consumption by number of pints, so I'll make one more conversion function.

``` r
# Create my function, ounces_to_pints
ounces_to_pints <- function(vol_oz) {
  num_pints <- vol_oz*0.0625
  return(num_pints)
}
```

How many pints are in 1 0.5 l Paulaner?

``` r
# I ususally have 16.907 fluid ounces. 
ounces_to_pints(16.907)
```

    ## [1] 1.056688

I've had just over one pint per beer. **So...how much beer have I been drinking in Gottingen?**!

    ## [1] "A lot."
