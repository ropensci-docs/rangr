# Convert `sim_results` To SpatRaster

Converts selected subset of abundance matrices from `sim_results` into
[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object. Layers are specified by `time_points`, which can be one or
multiple points in time.

## Usage

``` r
# S3 method for class 'sim_results'
to_rast(obj, time_points = obj$simulated_time, template = NULL, ...)
```

## Arguments

- obj:

  `sim_results` object created by
  [`sim`](https://docs.ropensci.org/rangr/reference/sim.md)

- time_points:

  numeric vector of length 1 or more; specifies points in time from
  which
  [`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
  will be created - as default the last year of simulation; if
  `length(time_points) > 0`
  [`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
  will be returned with layers for each element of `time_points`

- template:

  [`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
  object; can be used as a template to create returned object

- ...:

  Currently unused.

## Value

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
based on `sim_results` object with layers corresponding to
`time_points`.

## References

Hijmans R (2024). terra: Spatial Data Analysis. R package version
1.7-81, <https://rspatial.github.io/terra/>, <https://rspatial.org/>

## Examples

``` r
# \donttest{

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
sim_1 <- sim(obj = sim_data, time = 100)

# raster construction
my_rast <- to_rast(
  sim_1,
  time_points = c(1, 10, 20, 100),
  template = sim_data$K_map
)

# visualization
plot(my_rast, range = range(sim_1$N_map, na.rm = TRUE))


# }
```
