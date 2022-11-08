# ts.check

Data analysis should include a healthy dose of correctness checks:

- Did the data load correctly?
- Is the transformation doing what it's suppposed to do?
- Were the simulated values calculated correctly?

The first instinct is to do comparison of the form `x == 2.74`. This misses a couple of points. First, floating point comparisons like that can return the wrong result, so you should use `all.equal` or similar. Second, `all.equal` is not sufficient, because you need to convert `ts` objects using `as.numeric` prior to doing the comparison.

The purpose of  `ts.check` is to minimize the amount of this intermediate technical detail you need to know/understand.

# Signature

`ts.check <- function(x, dates, values)`

- `x`: A ts object. Currently, `x` needs to be a vector time series. In the future, this might be extended to allow checking of a matrix time series, but it does not do that at this time.
- `dates`: A list of dates to check.
- `values`: A vector of values that match the specified dates in `x`.

# Example

Test that four observations in `inf` have the correct value.

```
ts.check(inf, list(c(1959,11), c(2000,12),
    c(2008,1), c(2022,4)), c(10.6745, 2.79097, 15.62435, 10.57674))
# Second element shows a big difference
# Other elements slightly different due to rounding
# Returns TRUE if the check passes
```