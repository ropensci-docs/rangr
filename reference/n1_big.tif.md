# Example Of Abundance Map At First Time Step Of The Simulation (Big)

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object that can be used a as simulation starting point to
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
data necessary to perform a simulation with the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. This
map is compatible with
[`K_big.tif`](https://docs.ropensci.org/rangr/reference/K_big.tif.md)
map.

## Format

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object with 100 rows and 100 columns containing integer values 0-50 and
NA's that indicates unsuitable areas.

## Source

Data generated in-house to serve as an example.

## Examples

``` r
system.file("input_maps/n1_big.tif", package = "rangr")
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/rangr/input_maps/n1_big.tif"
```
