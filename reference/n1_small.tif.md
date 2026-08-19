# Example Of Abundance Map At First Time Step Of The Simulation (Small)

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object that can be used a as simulation starting point to
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
data necessary to perform a simulation with the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. This
map is compatible with
[`K_small.tif`](https://docs.ropensci.org/rangr/reference/K_small.tif.md)
and
[`K_small_changing.tif`](https://docs.ropensci.org/rangr/reference/K_small_changing.tif.md)
maps.

## Format

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object with 15 rows and 10 columns containing integer values 0-10 and
NA's indicating unsuitable areas.

## Source

Data generated in-house to serve as an example.

## Examples

``` r
system.file("input_maps/n1_small.tif", package = "rangr")
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/rangr/input_maps/n1_small.tif"
```
