# Example Of Changing Carrying Capacity Maps (Small)

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object representing changing carrying capacity maps projected to WGS 84
(CRS84) from the original raster `K_small_changing`. These maps can be
used as carrying capacity maps to
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
data necessary to perform a simulation with the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. To
utilise these maps in
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
the user must first use
[`K_get_interpolation`](https://docs.ropensci.org/rangr/reference/K_get_interpolation.md)
to generate a map for every time step of the simulation. These maps are
compatible with the `n1_small_lon_lat.tif` raster.

## Format

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object with 3 layers, each having 12 rows and 14 columns containing
integer values 0-170 and NA's indicating unsuitable areas.

## Source

Data generated in-house to serve as an example (using spatial
autocorrelation).

## Examples

``` r
system.file("input_maps/K_small_changing_lon_lat.tif", package = "rangr")
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/rangr/input_maps/K_small_changing_lon_lat.tif"
```
