# Summary Of `sim_results` Object

Summary Of `sim_results` Object

## Usage

``` r
# S3 method for class 'sim_results'
summary(object, ...)
```

## Arguments

- object:

  `sim_results` object; returned by
  [`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function

- ...:

  further arguments passed to or from other methods; none specified

## Value

`summary.sim_results` object

## Examples

``` r

# data preparation
library(terra)

n1_small <- rast(system.file("input_maps/n1_small.tif", package = "rangr"))
K_small <- rast(system.file("input_maps/K_small.tif", package = "rangr"))

sim_data <- initialise(
  n1_map = n1_small,
  K_map = K_small,
  r = log(2),
  rate = 1 / 1e3
)

# simulation
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
#>   0.000   0.000   0.000   1.176   1.000  28.000     120 
```
