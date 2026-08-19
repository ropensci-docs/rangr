# Generic conversion to SpatRaster

A generic method to convert simulation result objects into
[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
format.

## Usage

``` r
to_rast(obj, ...)
```

## Arguments

- obj:

  An object to convert.

- ...:

  Additional arguments passed to methods.

## Value

A
[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
or a list of such objects.

## See also

[`to_rast.sim_results()`](https://docs.ropensci.org/rangr/reference/to_rast.sim_results.md)

## Examples

``` r
if (FALSE) { # \dontrun{
to_rast(sim_results_object)
} # }
```
