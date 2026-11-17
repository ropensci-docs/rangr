# Simulating Dispersal

This function simulates dispersal for each grid cell by calculating the
number of individuals dispersing out of the cell and the number of
individuals dispersing into the cell.

## Usage

``` r
disp(
  N_t,
  id,
  id_matrix,
  data_table,
  kernel,
  dens_dep,
  dlist,
  id_within,
  within_mask,
  border,
  planar,
  dist_resolution,
  max_dist,
  dist_bin,
  ncells_in_circle,
  cl = NULL
)
```

## Arguments

- N_t:

  integer matrix representing population numbers at a single time step;
  NA indicates cells outside the study area

- id:

  [`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
  object (of the same size as `N_t`) with cell identifiers

- id_matrix:

  `id` in matrix format

- data_table:

  matrix that contains information about all cells in current time
  points

- kernel:

  function defining dispersal kernel

- dens_dep:

  character vector of length 1 specifying if the probability of settling
  in a target grid cell is (case-sensitive, default `"K2N"`):

  - "none" - fully random,

  - "K" - proportional to the carrying capacity of a target cell,

  - "K2N" - density-dependent, i.e. proportional to the ratio of
    carrying capacity of a target cell to the number of individuals
    already present in a target cell

- dlist:

  list with identifiers of target cells at a specified distance from a
  focal cell

- id_within:

  integer vector with identifiers of cells inside the study area

- within_mask:

  logical matrix that specifies boundaries of the study area

- border:

  character vector of length 1 defining how to deal with borders
  (case-sensitive, default `"absorbing"`):

  - "reprising" - cells outside the study area are not allowed as
    targets for dispersal

  - "absorbing" - individuals that disperse outside the study area are
    removed from the population

- planar:

  logical vector of length 1; `TRUE` if input maps are planar rasters,
  `FALSE` if input maps are lon/lat rasters

- dist_resolution:

  integer vector of length 1; dimension of one side of one cell of `id`;
  in case of an irregular grid or lon/lat raster it is calculated during
  [`initialisation`](https://docs.ropensci.org/rangr/reference/initialise.md)

- max_dist:

  distance (in the same units as used in the raster `id`) specifying the
  maximum range at which identifiers of target dispersal cells are
  determined in advance (see
  [`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md))

- dist_bin:

  numeric vector of length 1 with value `>= 0`; in case of an irregular
  grid or lon/lat raster it is calculated during
  [`initialisation`](https://docs.ropensci.org/rangr/reference/initialise.md)

- ncells_in_circle:

  numeric vector; number of cells on each distance

- cl:

  if simulation is done in parallel, the name of a cluster object
  created by
  [`makeCluster`](https://rdrr.io/r/parallel/makeCluster.html)

## Value

The function returns a list that contains two matrices:

`em` - emigration matrix with the number of individuals that dispersed
from each cell

`im` - immigration matrix with the number of individuals that dispersed
to each cell

## Details

The function is used by
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) internally and
is not intended to be called by the user. The parameters for this
function are passed from a `sim_data` object created by
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md).

Dispersal distance is expressed in original spatial units of the
[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
provided to the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function
(`n1_map` and `K_map`). However, it is internally converted to units of
the simulation (i.e. the size of a single cell) by calculating
`round(distance/resolution)`. If the selected dispersal distance is
smaller than `resolution/2`, the individual does not disperse
effectively and remains in the same cell. The dispersal rate (proportion
of dispersing individuals) can be estimated from the dispersal kernel
probability function by calculating the probability that the dispersal
distance is greater than `resolution/2`.

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

# disp
disp_output <- disp(
  N_t = sim_data$n1_map,
  id = unwrap(sim_data$id),
  id_matrix = as.matrix(unwrap(sim_data$id), wide = TRUE),
  data_table = sim_data$data_table,
  kernel = sim_data$kernel,
  dens_dep = sim_data$dens_dep,
  dlist = sim_data$dlist,
  id_within = sim_data$id_within,
  within_mask = sim_data$within_mask,
  border = sim_data$border,
  planar = sim_data$planar,
  dist_resolution = sim_data$dist_resolution,
  max_dist = sim_data$max_dist,
  dist_bin = sim_data$dist_bin,
  ncells_in_circle = sim_data$ncells_in_circle
)

# immigration and emigration matrices
names(disp_output)
#> [1] "em" "im"

```
