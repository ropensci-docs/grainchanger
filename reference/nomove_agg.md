# Direct data aggregation

Calculate the value for a given function for each cell in a larger
resolution grid.

## Usage

``` r
nomove_agg(coarse_dat, fine_dat, agg_fun, is_grid = TRUE, quiet = FALSE, ...)
```

## Arguments

- coarse_dat:

  sf, Raster\* or Spatial\* object. The coarse grain data (response
  data) across which to calculate the aggregated function

- fine_dat:

  Raster\* object. Raster\* object. The fine grain data (predictor /
  covariate data) to aggregate

- agg_fun:

  function The function to apply. The function fun should take multiple
  numbers, and return a single number. For example mean, modal, min or
  max. It should also accept a na.rm argument (or ignore it, e.g. as one
  of the 'dots' arguments. For example, length will fail, but
  function(x, ...)na.omit(length(x)) works. See Details

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

Raster (if input is Raster) or numeric vector (if input is sp or sf
object) containing values calculated for each coarser cell

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

Note that `nomove_agg` can be run in parallel using `plan(multiprocess)`
from the `future` package.

## Examples

``` r
# load required data
data(g_sf)
data(cont_ls)
data(cat_ls)

# aggregate using mean
d <- nomove_agg(g_sf, cont_ls, mean)
#> aggregation assumes all cells are rectangular
#> • set `is_grid = FALSE` if coarse_dat is not a grid

# aggregate using Shannon evenness
d <- nomove_agg(g_sf, cont_ls, shei, lc_class = 1:4)
#> aggregation assumes all cells are rectangular
#> • set `is_grid = FALSE` if coarse_dat is not a grid
```
