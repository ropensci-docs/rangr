# Prepare Data Required To Perform A Simulation

This function generates a `sim_data` object containing all the necessary
information required to run a simulation by the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. The
input maps (`n1_map` and `K_map`) can be in the Cartesian or
longitude/latitude coordinate system.

## Usage

``` r
initialise(
  n1_map,
  K_map,
  K_sd = 0,
  r,
  r_sd = 0,
  growth = "gompertz",
  A = NA,
  dens_dep = c("K2N", "K", "none"),
  border = c("reprising", "absorbing"),
  kernel_fun = "rexp",
  ...,
  max_dist = NA,
  calculate_dist = TRUE,
  dlist = NULL,
  progress_bar = TRUE,
  quiet = FALSE
)
```

## Arguments

- n1_map:

  [`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
  object with one layer; population numbers in every grid cell at the
  first time step

- K_map:

  [`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
  object with one layer; carrying capacity map (if K is constant across
  time) or maps (if K is time-varying)

- K_sd:

  numeric vector of length 1 with value `>= 0` (default 0); this
  parameter can be used if additional environmental stochasticity is
  required; if `K_sd > 0`, random numbers are generated from a
  log-normal distribution with the mean `K_map` and standard deviation
  `K_sd`

- r:

  numeric vector of length 1; intrinsic population growth rate

- r_sd:

  numeric vector of length 1 with value `>= 0` (default `0`); if
  additional demographic stochasticity is required, `r_sd > 0` is the
  standard deviation for a normal distribution around `r` (defined for
  each time step)

- growth:

  character vector of length 1; the name of a population growth
  function, either defined in
  [`growth`](https://docs.ropensci.org/rangr/reference/growth.md) or
  provided by the user (case-sensitive, default
  [`"gompertz"`](https://docs.ropensci.org/rangr/reference/growth.md))

- A:

  numeric vector of length 1; strength of the Allee effect (see the
  [`growth`](https://docs.ropensci.org/rangr/reference/growth.md)
  function)

- dens_dep:

  character vector of length 1 specifying if the probability of settling
  in a target grid cell is (case-sensitive, default `"K2N"`):

  - "none" - fully random,

  - "K" - proportional to the carrying capacity of a target cell,

  - "K2N" - density-dependent, i.e. proportional to the ratio of
    carrying capacity of a target cell to the number of individuals
    already present in a target cell

- border:

  character vector of length 1 defining how to deal with borders
  (case-sensitive, default `"absorbing"`):

  - "reprising" - cells outside the study area are not allowed as
    targets for dispersal

  - "absorbing" - individuals that disperse outside the study area are
    removed from the population

- kernel_fun:

  character vector of length 1; name of a random number generation
  function defining a dispersal kernel (case-sensitive, default
  `"rexp"`)

- ...:

  any parameters required by `kernel_fun`

- max_dist:

  numeric vector of length 1; maximum distance of dispersal to
  pre-calculate target cells

- calculate_dist:

  logical vector of length 1; determines if target cells will be
  precalculated

- dlist:

  list; target cells at a specified distance calculated for every cell
  within the study area

- progress_bar:

  logical vector of length 1; determines if progress bar for calculating
  distances should be displayed

- quiet:

  logical vector of length 1; determines if messages should be displayed

## Value

Object of class `sim_data` which inherits from `list`. This object
contains all necessary information to perform a simulation using
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function.

## Details

The most time-consuming part of computations performed by the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function is
the simulation of dispersal. To speed it up, a list containing indexes
of target cells at a specified distance from a focal cell is calculated
in advance and stored in a `dlist` slot. The `max_dist` parameter sets
the maximum distance at which this pre-calculation is performed. If
`max_dist` is `NULL`, it is set to 0.99 quantile from the `kernel_fun`.
All distance calculations are always based on metres if the input maps
are latitude/longitude. For planar input maps, distances are calculated
in map units, which are typically metres, but check the
[`crs()`](https://rspatial.github.io/terra/reference/crs.html) if in
doubt.

If the input maps are in the Cartesian coordinate system and the grid
cells are squares, then the distances between cells are calculated using
the
[`distance`](https://rspatial.github.io/terra/reference/distance.html)
function from the `terra` package. These distances are later divided by
the resolution of the input maps.

For input maps with grid cells in shapes other than squares (e.g. with
rectangular cells or longitude/latitude coordinate system), the distance
resolution is calculated by finding the shortest distance between each
"queen" type neighbor. All distances calculated by the
[`distance`](https://rspatial.github.io/terra/reference/distance.html)
function are further divided by this distance resolution. To avoid
discontinuities in the distances at which the target cells are located,
an additional parameter `dist_bin` is calculated as half of the maximum
distance between each "queen" type neighbour. It is used to expand the
distances at which target cells are located from a single number to a
range.

NA in the input maps represents cells outside the study area.

The
[`K_get_interpolation`](https://docs.ropensci.org/rangr/reference/K_get_interpolation.md)
function can be used to prepare `K_map` that changes over time. This may
be useful, when simulating environmental change or exploring the effects
of ecological disturbances.

## References

Hijmans R (2024). terra: Spatial Data Analysis. R package version
1.7-81, <https://rspatial.github.io/terra/>, <https://rspatial.org/>

Solymos P, Zawadzki Z (2023). pbapply: Adding Progress Bar to '\*apply'
Functions. R package version 1.7-2,
<https://CRAN.R-project.org/package=pbapply>.

## See also

[update](https://docs.ropensci.org/rangr/reference/update.sim_data.md)

## Examples

``` r
# \donttest{

# input maps
library(terra)

n1_small <- rast(system.file("input_maps/n1_small.tif", package = "rangr"))
K_small <- rast(system.file("input_maps/K_small.tif", package = "rangr"))
K_small_changing <- rast(system.file("input_maps/K_small_changing.tif",
                         package = "rangr"))
n1_small_lon_lat <- rast(system.file("input_maps/n1_small_lon_lat.tif", package = "rangr"))
K_small_lon_lat <- rast(system.file("input_maps/K_small_lon_lat.tif", package = "rangr"))

# basic example
sim_data_1 <- initialise(
  n1_map = n1_small,
  K_map = K_small,
  r = log(2),
  rate = 1 / 1e3
)

# example with changing environment
K_interpolated <- K_get_interpolation(
  K_small_changing,
  K_time_points = c(1, 25, 50)
)
#> Warning: Argument "time" is no specified - maximum from "K_time_points" is used as "time"

sim_data_2 <- initialise(
  n1_map = n1_small,
  K_map = K_interpolated,
  r = log(2),
  rate = 1 / 1e3
)

# example with lon/lat rasters
sim_data_3 <- initialise(
  n1_map = n1_small_lon_lat,
  K_map = K_small_lon_lat,
  r = log(2),
  rate = 1 / 1e3
)

# example without progress bar and messages
sim_data_4 <- initialise(
  n1_map = n1_small, K_map = K_small, K_sd = 0.1, r = log(5),
  r_sd = 4, growth = "ricker", rate = 1 / 200,
  max_dist = 5000, dens_dep = "K2N", progress_bar = FALSE, quiet = TRUE
)
# }

```
