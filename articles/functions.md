# Built-in functions

There are a number of built-in functions in the `grainchanger` package,
with their usage outlined below. While it is possible to use
user-defined functions within `winmove_agg`, `nomove_agg`, and
`winmove`, we welcome suggestions for additional functions. Please [add
as an issue](https://github.com/laurajanegraham/grainchanger/issues) -
doing it this way means we can maximise the speed of the function.

All functions can also be used on their own, either on an object of
class `winmove` or `numeric`.

When functions are used within `winmove_agg`, `winmove`, or directly on
an object of class `winmove`, they are calculated relative to within a
moving window.

When functions are used within `nomove_agg` all cells of `fine_dat`
within a given cell of `coarse_dat` are aggregated using the function.

## Current functions

| Function.Name | Description | Additional.arguments |
|:---|:---|:---|
| prop | Calculate the proportion of a given class | lc_class (numeric) |
| shdi | Calculate the Shannon diversity | lc_class (numeric) |
| shei | Calculate the Shannon evenness | lc_class (numeric) |
| var_range | Calculate the size of the range of values |  |

## Shannon diversity and evenness

Shannon diversity is calculated as
``` math
SHDI = -\sum_{i = 1}^m p_i lnp_i
```
where $`p_i`$ is the proportion of a given class $`i`$ of a total $`m`$
classes.

Shannon evenness is calculated as
``` math
SHEI = \frac{S}{ln(m)}
```

## Additional functions

We plan to add other useful functions to this small set of built-in
functions, such as relevant metrics from
[FRAGSTATS](https://www.umass.edu/landeco/research/fragstats/documents/fragstats.help.4.2.pdf).

We also welcome suggestions for additional functions. Please [add as an
issue](https://github.com/laurajanegraham/grainchanger/issues) - doing
it this way means we can maximise the speed of the function.
