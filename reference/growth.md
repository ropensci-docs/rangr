# Population Growth Functions

Population growth functions are used during simulation conducted by the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function. The
user is required to specify the name of a growth function while
initialising the `sim_data` object using
[`initialise`](https://docs.ropensci.org/rangr/reference/initialise.md).

## Usage

``` r
exponential(x, r, ...)

ricker(x, r, K, A = NA)

gompertz(x, r, K, A = NA)
```

## Arguments

- x:

  number of individuals

- r:

  intrinsic population growth rate

- ...:

  not used, added for compatibility reasons

- K:

  carrying capacity

- A:

  coefficient of Allee effect (A \<= 0: weak, A \> 0: strong, NA: none)

## Value

Object of the same dimensions as `x` that contains expected number of
individuals in the next time step.

## Details

`x` can be a vector, matrix,
[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
or any other `R` object for which basic arithmetic operations produce
valid results. These functions are intended to be used in the
[`sim`](https://docs.ropensci.org/rangr/reference/sim.md) function,
where `x` is a matrix of the same dimensions as the
[`SpatRaster`](https://rspatial.github.io/terra/reference/SpatRaster-class.html)
object specified in `n1_map` parameter.

## References

Boukal, D. S., & Berec, L. (2002). Single-species models of the Allee
effect: extinction boundaries, sex ratios and mate encounters. Journal
of Theoretical Biology, 218(3), 375-394.
[doi:10.1006/jtbi.2002.3084](https://doi.org/10.1006/jtbi.2002.3084)

Gompertz, B. (1825) On the Nature of the Function Expressive of the Law
of Human Mortality, and on a New Mode of Determining the Value of Life
Contigencies. Philosophical Transactions of the Royal Society of London,
115, 513-583.
[doi:10.1098/rstl.1825.0026](https://doi.org/10.1098/rstl.1825.0026)

Ricker, W.E. (1954) Stock and Recruitment. Journal of the Fisheries
Research Board of Canada, 11, 559-623.
[doi:10.1139/f54-039](https://doi.org/10.1139/f54-039)

Hostetler, J.A. and Chandler, R.B. (2015), Improved state-space models
for inference about spatial and temporal variation in abundance from
count data. Ecology, 96: 1713-1723.
[doi:10.1890/14-1487.1](https://doi.org/10.1890/14-1487.1)

Courchamp, F., L. Berec and J. Gascoigne. 2008. Allee Effects in Ecology
and Conservation. Oxford University Press, New York. 256 pp. ISBN
978-0-19-857030-1

## Examples

``` r
x <- 1:10
exponential(x, r = 0.4)
#>  [1]  1.491825  2.983649  4.475474  5.967299  7.459123  8.950948 10.442773
#>  [8] 11.934598 13.426422 14.918247

ricker(x, r = 2, K = 5)
#>  [1] 4.953032 6.640234 6.676623 5.967299 5.000000 4.021920 3.145303 2.409554
#>  [9] 1.817069 1.353353
ricker(x, r = 2, K = 5, A = -5)
#>  [1]  6.82095847 10.73111194 10.78991918  8.21773284  5.00000000  2.48869747
#>  [7]  1.02624873  0.35325735  0.10200072  0.02478752

gompertz(x, r = 1.2, K = 5)
#>  [1] 2.087102 3.181557 3.936002 4.519499 5.000000 5.411464 5.773278 6.097557
#>  [9] 6.392388 6.663442
gompertz(x, r = 1.2, K = 5, A = 5)
#>  [1] 0.5550921 1.5137850 2.6912102 3.9034978 5.0000000 5.8773825 6.4807880
#>  [8] 6.7971920 6.8450876 6.6634415
```
