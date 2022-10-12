# trim.dates

`trim.dates <- function(x,y)`

Returns a copy of `x` that is trimmed so the dates match those of `y`. 

- The start date for the returned copy of `x` is the later of the start dates of `x` and `y`. 
- The end date is the earlier of the end dates of `x` and `y`.
- `y` can be an mts object (time series with multiple variables).

Example:

```
# x is monthly from 2010:01 to 2022:02
# y is monthly from 2010:06 to 2022:10
# These are equivalent
trim.dates(x, y)
window(x, start=c(2010,6), end=c(2022,2))
# As are these
trim.dates(y, x)
window(y, start=c(2010,6), end=c(2022,2))
```