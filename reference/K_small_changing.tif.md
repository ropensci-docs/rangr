# Example Of Changing Carrying Capacity Maps (Small)

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object that can be used as carrying capacity maps to
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
data necessary to perform a simulation with the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. To
utilise these maps in
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md)
the user first must use
[`K_get_interpolation`](https://docs.ropensci.org/rangr/reference/K_get_interpolation.md)
to generate a map for every time step of the simulation. These maps are
compatible with
[`n1_small.tif`](https://docs.ropensci.org/rangr/reference/n1_small.tif.md).
Each subsequent map contains a virtual environment with greater carrying
capacity than the previous one.

## Format

[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object with 3 layers, each has 15 rows and 10 columns containing integer
values 0-170 and NA's that indicates unsuitable areas.

## Source

Data generated in-house to serve as an example (using spatial
autocorrelation).

## Examples

``` r
system.file("input_maps/K_small_changing.tif", package = "rangr")
#> [1] "/github/home/R/x86_64-pc-linux-gnu-library/4.6/rangr/input_maps/K_small_changing.tif"
```
