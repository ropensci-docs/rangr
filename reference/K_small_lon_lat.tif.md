# Example Of Carrying Capacity Map (Small)

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object that represents a carrying capacity map projected to WGS 84
(CRS84) from the original raster `K_small`. This map can be used as a
carrying capacity map to
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
data necessary to perform a simulation with the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. It
is compatible with the `n1_small_lon_lat.tif` raster.

## Format

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object with 12 rows and 14 columns containing integer values 0-100 and
NA's indicating unsuitable areas.

## Source

Data generated in-house to serve as an example (using spatial
autocorrelation).

## Examples

``` r
system.file("input_maps/K_small_lon_lat.tif", package = "rangr")
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/rangr/input_maps/K_small_lon_lat.tif"
```
