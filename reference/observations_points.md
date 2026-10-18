# Example Of Observation Points List

A `data.frame` containing a sample input data to the function
[`get_observations`](https://docs.ropensci.org/rangr/reference/get_observations.md)
when `type` argument is set to "from_file". This data is compatible with
[`n1_small.tif`](https://docs.ropensci.org/rangr/reference/n1_small.tif.md),
[`K_small.tif`](https://docs.ropensci.org/rangr/reference/K_small.tif.md)
and
[`K_small_changing.tif`](https://docs.ropensci.org/rangr/reference/K_small_changing.tif.md)
maps.

## Usage

``` r
observations_points
```

## Format

A data frame with 1500 rows and 3 variables:

- x:

  x coordinate

- y:

  y coordinate

- time_step:

  time_step at which the abundances should be observed

## Source

Data generated in-house to serve as an example
