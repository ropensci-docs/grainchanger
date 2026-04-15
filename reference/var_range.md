# Size of range of values

Calculates the difference between the maximum and minimum value

## Usage

``` r
var_range(x, ...)

# S3 method for class 'winmove'
var_range(x, d, type, na.rm = TRUE, ...)

# S3 method for class 'numeric'
var_range(x, na.rm = TRUE, ...)
```

## Arguments

- x:

  RasterLayer. The data over which to calculate the range size

- ...:

  further arguments passed to or from other methods

- d:

  numeric. If `type=circle`, the radius of the circle (in units of the
  CRS). If `type=rectangle` the dimension of the rectangle (one or two
  numbers)

- type:

  character. The shape of the moving window

- na.rm:

  logical. indicates whether `NA` values should be stripped before the
  computation proceeds. `na.rm = TRUE` is the default

## Value

If `class(x) == "winmove"`, a smoothed raster with the size of the range
of values calculated within the specified moving window

If `class(x) == "numeric"`, a single value representing the size of the
range of values in `x`

## Examples

``` r
# load required data
data(cat_ls)
data(cont_ls)

# convert data to object of class winmove
cat_ls <- new("winmove", cat_ls)
#> Error in methods::slot(value, what): no slot of name "srs" for this object of class "RasterLayer"

# aggregate using a rectangular window with dimensions c(2,3)
d <- range(cont_ls, d = c(2,3), type = "rectangle")
#> Warning: Nothing to summarize if you provide a single RasterLayer; see cellStats

# convert data to object of class numeric
cont_ls <- raster::values(cont_ls)
d <- range(cont_ls)
```
