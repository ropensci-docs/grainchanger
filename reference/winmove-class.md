# An S4 class for use with winmove functions (extends RasterLayer)

An S4 class for use with winmove functions (extends RasterLayer).
Objects will need to be set to this class in order to be used with the
inbuilt `winmove` functions (e.g. `mean`, `prop`, `var_range`, `shdi`,
`shei`)

## Slots

Slots for RasterLayer and RasterBrick objects

- `title`::

  Character

- `file`::

  Object of class `".RasterFile"`

- `data`::

  Object of class `".SingleLayerData"` or `".MultipleLayerData"`

- `history`::

  To record processing history, not yet in use

- `legend`::

  Object of class `.RasterLegend`, Default legend. Should store
  preferences for plotting. Not yet implemented except that it stores
  the color table of images, if available

- `extent`::

  Object of
  [`Extent-class`](https://rdrr.io/pkg/raster/man/Extent-class.html)

- `ncols`::

  Integer

- `nrows`::

  Integer

- `crs`::

  Object of class `"CRS"`, i.e. the coordinate reference system. In
  Spatial\* objects this slot is called 'proj4string'

## Examples

``` r
# load required data
data(cat_ls)

# set \code{cat_ls} to object of class winmove
new("winmove", cat_ls)
#> Error in methods::slot(value, what): no slot of name "srs" for this object of class "RasterLayer"
```
