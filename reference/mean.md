# Arithmetic mean

An extension to `mean` for objects of class `winmove`

## Usage

``` r
mean(x, ...)

# S3 method for class 'winmove'
mean(x, d, type, ...)
```

## Arguments

- x:

  RasterLayer. The data over which to calculate the mean value within a
  moving window

- ...:

  further arguments passed to or from other methods

- d:

  numeric. If `type=circle`, the radius of the circle (in units of the
  CRS). If `type=rectangle` the dimension of the rectangle (one or two
  numbers)

- type:

  character. The shape of the moving window

## Value

RasterLayer. A smoothed raster with the mean calculated within the
specified moving window

## Examples

``` r
# load required data
data(cont_ls)

# convert data to object of class winmove
cont_ls <- new("winmove", cont_ls)
#> Error in methods::slot(value, what): no slot of name "srs" for this object of class "RasterLayer"

# aggregate using a circular window with radius 3
d <- mean(cont_ls, d = 3, type = "circle")
#> Warning: argument is not numeric or logical: returning NA
```
