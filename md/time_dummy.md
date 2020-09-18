# time.dummy

Create a time series dummy variable.

## Arguments

`time.dummy <- function(x, dates1, dates2=NULL)`

- `x`: The time series for which you want to create a matching dummy variable.
- `dates1` and `dates2`: See below.

If `dates1` is a single date and `dates2` is `NULL`, this function creates
a dummy variable equal to `TRUE` for that single date.

If `dates1` is a list of dates and `dates2` is `NULL`, creates a dummy
variable equal to `TRUE` on each date in `dates1`.

If `dates2` is a single date and `dates2` is a single date, creates a
dummy variable equal to `TRUE` for all dates in that range.

If `dates1` is "start", sets `dates1` to the first observation.

If `dates2` is "end", sets `dates2` to the last observation.

# Examples

```
time.dummy(y, c(2004,7)) # One observation is TRUE
time.dummy(y, c(2004,7), c(2005,8)) # 14 observations are TRUE
time.dummy(y, "start", c(2005,8))
time.dummy(y, c(2004,7), "end")
time.dummy(y, "start", "end") # Legal, but doesn't make any sense
time.dummy(y, list(c(2003,8), c(2004,9), c(2009, 12))) # Three observations are TRUE
```
