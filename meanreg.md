# meanreg

Do a regression to get the mean of a ts object. There are a couple
reasons you might use this function rather than calling `mean`.

- `meanreg` provides standard errors.
- `meanreg` allows you to more easily specify start and/or end dates.

## Arguments

`meanreg <- function(y, start=NULL, end=NULL)`

- y: A time series.
- start: Optional start of the time series.
- end: Optional end of the time series.

## Examples

```
x <- ts(rnorm(120), start=c(2010,1), frequency=12)
meanreg(x) # mean
meanreg(x, start=c(2014,1)) # mean of x from Jan 2014 to the end
meanreg(x, end=c(2017,4)) # mean of x through Apr 2017
meanreg(x, start=c(2014,1), end=c(2017,4))
```
