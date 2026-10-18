# Print `sim_data` Object

Print `sim_data` Object

## Usage

``` r
# S3 method for class 'sim_data'
print(x, ...)
```

## Arguments

- x:

  `sim_data` object; returned by the
  [`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
  function

- ...:

  further arguments passed to or from other methods; currently none
  specified

## Value

`sim_data` object is invisibly returned (the `x` param)

## Examples

``` r

library(terra)

n1_small <- rast(system.file("input_maps/n1_small.tif", package = "rangr"))
K_small <- rast(system.file("input_maps/K_small.tif", package = "rangr"))

sim_data <- initialise(
  n1_map = n1_small,
  K_map = K_small,
  r = log(2),
  rate = 1 / 1e3
)
print(sim_data)
#> Class: sim_data
#> 
#> n1_map:
#>    Min. 1st Qu.  Median    Mean 3rd Qu.    Max.     NAs 
#>  0.0000  0.0000  0.0000  0.1449  0.0000 10.0000      12 
#> 
#> K_map:
#> class       : SpatRaster
#> size        : 15, 10, 1  (nrow, ncol, nlyr)
#> resolution  : 1000, 1000  (x, y)
#> extent      : 270000, 280000, 610000, 625000  (xmin, xmax, ymin, ymax)
#> coord. ref. : ETRS89 / Poland CS92
#> source(s)   : memory
#> varname     : K_small
#> name        : layer
#> min value   :     0
#> max value   :   100
#>                             
#> r          0.693147180559945
#> r_sd                       0
#> K_sd                       0
#> growth              gompertz
#> A                          -
#> dens_dep                 K2N
#> border             reprising
#> max_dist                4000
#> kernel_fun              rexp
#> dlist                   TRUE
```
