# Example Of Carrying Capacity Map (Small)

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object that can be used a carrying capacity map to
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
data necessary to perform a simulation with the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. This
map is compatible with
[`n1_small.tif`](https://docs.ropensci.org/rangr/reference/n1_small.tif.md).

## Format

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object with 15 rows and 10 columns containing integer values 0-100 and
NA's indicating unsuitable areas.

## Source

Data generated in-house to serve as an example (using spatial
autocorrelation).

## Examples

``` r
system.file("input_maps/K_small.tif", package = "rangr")
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/rangr/input_maps/K_small.tif"
```
