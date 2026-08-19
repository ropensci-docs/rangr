# Update `sim_data` Object

This function updates a `sim_data` object.

## Usage

``` r
# S3 method for class 'sim_data'
update(object, ..., evaluate = TRUE)
```

## Arguments

- object:

  `sim_data` object; returned by
  [`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
  function

- ...:

  further arguments passed to or from other methods; currently none
  specified

- evaluate:

  logical vector of length 1; if `TRUE` evaluates the new call,
  otherwise returns the call

## Value

If `evaluate = TRUE` then the updated `sim_data` object, otherwise the
updated call.

## Examples

``` r
# \donttest{

# data preparation
library(terra)
n1_small <- rast(system.file("input_maps/n1_small.tif", package = "rangr"))
K_small <- rast(system.file("input_maps/K_small.tif", package = "rangr"))

sim_data_1 <- initialise(
  n1_map = n1_small,
  K_map = K_small,
  r = log(2),
  rate = 1 / 1e3
)
summary(sim_data_1)
#> Summary of sim_data object
#> 
#> n1 map summary: 
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>  0.0000  0.0000  0.0000  0.1449  0.0000 10.0000      12 
#> 
#> Carrying capacity map summary: 
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>    0.00    0.00   56.00   44.84   72.00  100.00      12 
#>                       
#> growth        gompertz
#> r               0.6931
#> A                    -
#> kernel_fun        rexp
#> dens_dep           K2N
#> border       reprising
#> max_dist          5000
#> changing_env     FALSE
#> dlist             TRUE

sim_data_2 <- update(sim_data_1, max_dist = 3000)
summary(sim_data_2)
#> Summary of sim_data object
#> 
#> n1 map summary: 
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>  0.0000  0.0000  0.0000  0.1449  0.0000 10.0000      12 
#> 
#> Carrying capacity map summary: 
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>    0.00    0.00   56.00   44.84   72.00  100.00      12 
#>                       
#> growth        gompertz
#> r               0.6931
#> A                    -
#> kernel_fun        rexp
#> dens_dep           K2N
#> border       reprising
#> max_dist          3000
#> changing_env     FALSE
#> dlist             TRUE

# }
```
