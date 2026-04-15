# Calculate proportion of a given value

Calculate the proportion of a given value present within a raster.
Useful for calculating land-cover or soil type proportions. Should be
used with a categorical raster

## Usage

``` r
prop(x, lc_class, ...)

# S3 method for class 'winmove'
prop(x, lc_class, d, type, ...)

# S3 method for class 'numeric'
prop(x, lc_class, ...)
```

## Arguments

- x:

  numeric, winmove. The data over which to calculate the proportion

- lc_class:

  numeric. The class value to calculate the proportion of

- ...:

  further arguments passed to or from other methods

- d:

  numeric. If `type=circle`, the radius of the circle (in units of the
  CRS). If `type=rectangle` the dimension of the rectangle (one or two
  numbers)

- type:

  character. The shape of the moving window

## Value

If `class(x) == "winmove"`, a smoothed raster with the proportion of
cells of the given class calculated within the specified moving window

If `class(x) == "numeric"`, a single value representing the proportion
of values of a given class in `x`

## Examples

``` r
# load required data
data(cat_ls)

# convert data to object of class winmove
cat_ls <- new("winmove", cat_ls)
#> Error in methods::slot(value, what): no slot of name "srs" for this object of class "RasterLayer"

# aggregate using a rectangular window with dimension 5 for class 3
d <- prop(cat_ls, d = 5, type = "rectangle", lc_class = 3)
#> Error in UseMethod("prop"): no applicable method for 'prop' applied to an object of class "c('RasterLayer', 'Raster', 'BasicRaster')"

# convert data to object of class numeric
cat_ls <- raster::values(cat_ls)
d <- prop(cat_ls, lc_class = 2)
```
