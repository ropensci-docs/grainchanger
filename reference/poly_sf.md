# Example polygon (coarse_dat)

An example non-gridded coarse data to show functionality when
aggregating using an sf object.

## Usage

``` r
poly_sf
```

## Format

An sf object.

## Details

Generated with
`sf::st_make_grid(sf::st_as_sfc(sf::st_bbox(cont_ls)), cellsize = 13, square = FALSE)`
