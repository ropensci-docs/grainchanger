# Create moving window surface

Smooth a raster surface using a moving window with a given function,
radius and shape.

## Usage

``` r
winmove(fine_dat, d, type = c("circle", "rectangle"), win_fun, ...)
```

## Arguments

- fine_dat:

  The raster dataset on which to calculate the moving window function

- d:

  numeric. If `type=circle`, the radius of the circle (in units of the
  CRS). If `type=rectangle` the dimension of the rectangle (one or two
  numbers).

- type:

  The shape of the moving window

- win_fun:

  function. The function to apply. If not choosing one of the inbuilt
  grainchanger functions, the function should take multiple numbers, and
  return a single number. For example `mean`, `modal`, `min` or `max`.
  It should also accept a `na.rm` argument (or ignore it, e.g. as one of
  the 'dots' arguments. For example, length will fail, but
  `function(x, ...){na.omit(length(x))}` works. See Details

- ...:

  further arguments passed to or from other methods

## Value

RasterLayer. A smoothed raster with the moving window values calculated

## Details

`grainchanger` has several built-in functions. Functions currently
included are:

- `wm_shei` - Shannon evenness, requires the additional argument
  `lc_class` (vector or scalar)

- `wm_prop` - Proportion, requires the additional argument `lc_class`
  (scalar)

- `wm_classes` - Unique number of classes in a categorical landscape

- `var_range` - Range (max - min)

## Examples

``` r
# load required data
data(cat_ls)
data(cont_ls)

# calculate the moving window mean
d <- winmove(cont_ls, 5, "rectangle", mean)
#> Error in methods::slot(value, what): no slot of name "srs" for this object of class "RasterLayer"

# calculate the moving window Shannon evenness
d <- winmove(cat_ls, 5, "rectangle", shei, lc_class = 1:4)
#> Error in methods::slot(value, what): no slot of name "srs" for this object of class "RasterLayer"
```
