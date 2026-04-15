# Moving-window data aggregation

Calculate the mean moving window value for a given radius, shape and
function for each cell in a larger resolution grid.

## Usage

``` r
winmove_agg(
  coarse_dat,
  fine_dat,
  d,
  type = c("circle", "rectangle"),
  win_fun,
  agg_fun = mean,
  is_grid = TRUE,
  quiet = FALSE,
  ...
)
```

## Arguments

- coarse_dat:

  sf, Raster\* or Spatial\* object. The coarse grain data (response
  data) across which to calculate the aggregated moving window function

- fine_dat:

  Raster\* object. The fine grain data (predictor / covariate data) to
  aggregate

- d:

  numeric. If `type=circle`, the radius of the circle (in units of the
  CRS). If `type=rectangle` the dimension of the rectangle (one or two
  numbers).

- type:

  character. The shape of the moving window

- win_fun:

  character. The function to apply to the moving window. The function
  `win_fun` should take multiple numbers, and return a single number.
  For example `mean`, `modal`, `min` or `max`. It should also accept a
  `na.rm` argument (or ignore it, e.g. as one of the 'dots' arguments.
  For example, `length` will fail, but
  `function(x, ...){na.omit(length(x))}` works. See Details

- agg_fun:

  character. The function by which to aggregate. By default this is set
  to `mean`

- is_grid:

  logical. Use `TRUE` (default) if `g` contains only rectangular cells
  (i.e. a grid). If `g` is any other polygon file, this should be set to
  false

- quiet:

  logical. If `FALSE` (default) and `is_grid == TRUE` the user gets a
  warning that the aggregation assumes all cells are rectangular

- ...:

  further arguments passed to or from other methods

## Value

Numeric vector containing moving window values calculated for each grid
cell

## Details

`grainchanger` has several built-in functions. Functions currently
included are:

- `shdi` - Shannon diversity, requires the additional argument
  `lc_class` (vector or scalar)

- `shei` - Shannon evenness, requires the additional argument `lc_class`
  (vector or scalar)

- `prop` - Proportion, requires the additional argument `lc_class`
  (scalar)

- `var_range` - Range (max - min)

Note that `winmove_agg` can be run in parallel using
`plan(multiprocess)` from the `future` package.

## Examples

``` r
if (FALSE) { # \dontrun{
# load required data
data(g_sf)
data(cont_ls)
data(cat_ls)

# aggregate using mean
d <- winmove_agg(g_sf, cont_ls, 5, "rectangle", mean)

# aggregate using Shannon evenness
d <- winmove_agg(g_sf, cat_ls, 5, "rectangle", shei, lc_class = 1:4)
} # }
```
