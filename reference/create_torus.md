# Pad a raster by a specified radius

This function pads a raster by a specified number of cells, creating the
effect of a torus. This function is intended for use on simulated
landscapes, in order to avoid edge effects

## Usage

``` r
create_torus(dat, dpad)
```

## Arguments

- dat:

  The raster dataset to pad

- dpad:

  The amount by which to pad the raster (in the same units as the
  raster)

## Value

raster. Original raster padded by r cells with torus effect (see
Details)

## Details

A torus is an infinite surface where the top joins the bottom, and the
left side meets the right side. See https://en.wikipedia.org/wiki/Torus
for a full mathematical description.

In this function, the torus effect is achieved by adding the specified
number of rows of the top of the raster to the bottom (and vice versa)
and the specified number of rows of the right of the raster to the left
(and vice versa)

## Examples

``` r
data(cat_ls)
d <- create_torus(dat = cat_ls, dpad = 5)
```
