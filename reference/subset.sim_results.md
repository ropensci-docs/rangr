# Subset of Given Time Points from `sim_results` Object

This function creates a subset of given time points from the
`sim_results` object.

## Usage

``` r
# S3 method for class 'sim_results'
subset(x, from = NULL, time_points = NULL, ...)
```

## Arguments

- x:

  `sim_results` object; returned by the
  [`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function

- from:

  numeric vector of length 1; indicates the starting time point from
  which all time point should be kept

- time_points:

  numeric vector; indicates all time points to keep

- ...:

  further arguments to be passed to or from other methods

## Value

`sim_results` object with only selected `time_points` present in the
`N_map` slot

## Details

Either `from` or `time_points` argument has to be specified. Time point
passed by the `from` argument will be set as a cutoff point and all
abundances for previous time points will be discarded.

## Examples

``` r
# data preparation
library(terra)

n1_small <- rast(system.file("input_maps/n1_small.tif", package = "rangr"))
K_small <- rast(system.file("input_maps/K_small.tif", package = "rangr"))

sim_data <- initialise(
  n = n1_small,
  r = log(2),
  K_map = K_small,
  max_dist = 1000,
  rate = 1 / 1e3
)

sim_results <- sim(sim_data, time = 10)
summary(sim_results)

#> Summary of sim_results object
#> 
#> Simulation summary: 
#>                     
#> simulated time    10
#> extinction     FALSE
#> 
#> Abundances summary: 
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>   0.000   0.000   0.000   1.089   1.000  17.000     120 

sim_results_cropped <- subset(sim_results, time_points = c(1:2))
summary(sim_results_cropped)

#> Summary of sim_results object
#> 
#> Simulation summary: 
#>                     
#> simulated time     2
#> extinction     FALSE
#> 
#> Abundances summary: 
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>  0.0000  0.0000  0.0000  0.1268  0.0000 10.0000      24 

```
