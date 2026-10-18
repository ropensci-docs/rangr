# Example Of Abundance Map At First Time Step Of The Simulation (Small)

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object representing an abundance map at the first time step of the
simulation projected to WGS 84 (CRS84) from the original raster
`n1_small`. This map can be used as a simulation starting point to
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
data necessary to perform a simulation with the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. It
is compatible with the `K_small_lon_lat.tif` and
`K_small_changing_lon_lat.tif` maps.

## Format

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object with 12 rows and 14 columns containing integer values 0-10 and
NA's indicating unsuitable areas.

## Source

Data generated in-house to serve as an example.

## Examples

``` r
system.file("input_maps/n1_small_lon_lat.tif", package = "rangr")
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/rangr/input_maps/n1_small_lon_lat.tif"
```
