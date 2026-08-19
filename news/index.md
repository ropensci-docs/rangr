# Changelog

## rangr 1.0.10 (2026-08-18)

- Fixed bug with `update` when `sim_data` has `K_sim` with more than 1
  layer

- Updated documentation

## rangr 1.0.9 (2026-01-22)

CRAN release: 2026-01-23

- Updated DESCRIPTION: Added funding information

- Changed `n1_map` slot in `sim_data` object to integer matrix

## rangr 1.0.8 (2025-12-03)

CRAN release: 2025-12-17

#### Minor improvements

- `N_map` slot stored as integer instead of double in `sim_results`

## rangr 1.0.7 (2025-05-23)

CRAN release: 2025-05-26

#### Minor improvements

- `to_rast` is now a method of `sim_results`

- Updated installation instructions

## rangr 1.0.6 (2025-02-26)

CRAN release: 2025-02-26

#### Minor improvements

- Updated Description

- Updated tests

## rangr 1.0.5 (2024-08-09)

CRAN release: 2025-02-14

#### Minor improvements

- Added references to documentation (`growth`, `initialise`, `to_rast`)

- Added more comments inside functions

- Updated readme (lon/lat data)

- Updated documentation (examples and some clarifications)

## rangr 1.0.4 (2024-05-30)

#### Major improvements

- Added support for lon/lat rasters as input maps

#### Minor improvements

- Default value of `max_dist` in
  [`initialise()`](https://docs.ropensci.org/rangr/reference/initialise.md)
  is now equal to 0.99 quantile of `kernel_fun` instead of 0.9

- Added examples of lon/lat rasters to package data

- Input maps (`K_map` and `n1_map`) are now wrapped in `sim_data` object

## rangr 1.0.3 (2024-01-23)

#### Minor improvements

- Remove [`print()`](https://rdrr.io/r/base/print.html) from the
  vignette

- All messages produced during
  [`initialise()`](https://docs.ropensci.org/rangr/reference/initialise.md)
  are now turned off by default (by `quiet` parameter)

- Changed the appearance of the progress bar in the
  [`sim()`](https://docs.ropensci.org/rangr/reference/sim.md) function
  to match that in
  [`initialise()`](https://docs.ropensci.org/rangr/reference/initialise.md)

- In
  [`summary.sim_data()`](https://docs.ropensci.org/rangr/reference/summary.sim_data.md)
  the `r` parameter is now rounded to the 4th decimal place

## rangr 1.0.2 (2024-01-16)

#### Major improvements

- `rangr` is now based on the `terra` package

- Added binomial distribution to `get_observation()` (new distribution
  defining the observation process)

#### Minor improvements

- Added more default values for
  [`initialize()`](https://rdrr.io/r/methods/new.html)’s parameters

- Improved documentation for `get_observation()`

- Improved documentation - titles formatting

- Added more examples to
  [`plot.sim_results()`](https://docs.ropensci.org/rangr/reference/plot.sim_results.md)

## rangr 1.0.1 (2023-09-04)

#### Minor improvements

- Improved documentation for
  [`get_observations()`](https://docs.ropensci.org/rangr/reference/get_observations.md).

- Added functionality description for
  [`get_observations()`](https://docs.ropensci.org/rangr/reference/get_observations.md)
  to the vignettes
