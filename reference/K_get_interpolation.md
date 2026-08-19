# Prepare Time-Varying Carrying Capacity Maps

This function linearly interpolates values in a series of carrying
capacity maps.

## Usage

``` r
K_get_interpolation(K_map, K_time_points = NULL, time = NULL)
```

## Arguments

- K_map:

  [`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
  object with carrying capacity maps for each `K_time_points`

- K_time_points:

  integer vector; time for each layer in `K_map`, should contain unique
  values

- time:

  integer vector of length 1; number of total time steps required (this
  is defined when evoking the function
  [`sim`](https://docs.ropensci.org/rangr/reference/sim.md)).

## Value

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object with number of layers equal to `time`.

## Details

To simulate dynamic environmental scenarios (e.g. climate change, land
use change, ecological disturbance, etc.) one needs to provide
time-varying carrying capacity maps.

Either `K_time_points` or the `time` parameter is needed to perform
interpolation. If the interpolation should be calculated between two
carrying capacity maps, there is no need to pass the time points,
because 1 will be set as the starting time point and `time` will be used
as the ending point. On the other hand, in the absence of the `time`
argument, the maximum element of `K_time_points` is considered to be the
ending point for the interpolation.

## Examples

``` r

# data preparation
library(terra)
#> terra 1.9.34

n1_small <- rast(system.file("input_maps/n1_small.tif", package = "rangr"))
K_small_changing <- rast(system.file("input_maps/K_small_changing.tif",
package = "rangr"))

K_interpolated_01 <- K_get_interpolation(
  K_small_changing,
  K_time_points = c(1, 10, 15)
)
#> Warning: Argument "time" is no specified - maximum from "K_time_points" is used as "time"

K_two_layers <- subset(
  K_small_changing,
  c(1, 2)
)
K_interpolated_02 <- K_get_interpolation(
  K_two_layers,
  time = 15
)

```
