# Diversity metrics

A range of functions to calculate well known landcover diversity metrics

## Usage

``` r
# S3 method for class 'winmove'
shdi(x, lc_class, d, type, ...)

# S3 method for class 'numeric'
shdi(x, lc_class, ...)

# S3 method for class 'winmove'
shei(x, lc_class, d, type, ...)

# S3 method for class 'numeric'
shei(x, lc_class, ...)
```

## Arguments

- x:

  numeric, winmove. The data over which to calculate the diversity
  metrics

- lc_class:

  numeric. The class values to include in the diversity metric
  calculation

- d:

  numeric. If `type=circle`, the radius of the circle (in units of the
  CRS). If `type=rectangle` the dimension of the rectangle (one or two
  numbers)

- type:

  character. The shape of the moving window

- ...:

  further arguments passed to or from other methods

## Value

If `class(x) == "winmove"`, a smoothed raster with the diversity metric
calculated within the specified moving window

If `class(x) == "numeric"`, a single value representing the diversity
metric in `x`

## Details

Currently provided diversity metrics are Shannon diversity and Shannon
evenness. Open a new issue
(https://github.com/laurajanegraham/grainchanger/issues) to request
additional diversity metrics.

## References

McGarigal, K. and Marks, B.J., 1995. FRAGSTATS: spatial pattern analysis
program for quantifying landscape structure. *Gen. Tech. Rep.
PNW-GTR-351. Portland, OR: US Department of Agriculture, Forest Service,
Pacific Northwest Research Station. 122 p, 351.*

## Examples

``` r
# load required data
data(cat_ls)

# convert data to object of class winmove
cat_ls <- new("winmove", cat_ls)
#> Error in methods::slot(value, what): no slot of name "srs" for this object of class "RasterLayer"

# calculate Shannon diversity in a rectangular window of dimension 5
d <- shdi(cat_ls, d = 5, type = "rectangle", lc_class = 1:4)
#> Error in UseMethod("shdi"): no applicable method for 'shdi' applied to an object of class "c('RasterLayer', 'Raster', 'BasicRaster')"

# convert data to object of class numeric
cat_ls <- raster::values(cat_ls)

# calculate Shannon evenness
d <- shei(cat_ls, lc_class = 1:4)
```
