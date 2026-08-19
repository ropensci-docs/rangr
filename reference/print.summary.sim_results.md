# Print `summary.sim_results` Object

Print `summary.sim_results` Object

## Usage

``` r
# S3 method for class 'summary.sim_results'
print(x, ...)
```

## Arguments

- x:

  `summary.sim_results` object; returned by
  [`summary.sim_results`](https://docs.ropensci.org/rangr/reference/summary.sim_results.md)
  function

- ...:

  further arguments passed to or from other methods; currently none
  specified

## Value

None

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
sim_results <- sim(sim_data, time = 10)
summary_sim_results <- summary(sim_results)

print(summary_sim_results)
#> Summary of sim_results object
#> 
#> Simulation summary: 
#>                     
#> simulated time    10
#> extinction     FALSE
#> 
#> Abundances summary: 
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>   0.000   0.000   0.000   1.153   1.000  23.000     120 
```
