# tsreg

Does a time series regression. Different from `lm`. `lm` is a general regression function, so
it doesn't do what you want for time series regression. `tsreg` returns
the following in its output:

- Everything in `lm` output.
- `$resids`: The residuals (as a ts object)
- `$fitted`: The fitted values (as a ts object)
- `$start`: The first observation used in the regression data.
- `$end`: The last observation used in the regression data.
- `$int`: `TRUE` or `FALSE` to denote whether there's an intercept in the regression.

# Arguments

`tsreg <- function(y.raw, x.raw, start=NULL, end=NULL, intercept=TRUE)`

- `y.raw`: A ts object. The left side of the regression.
- `x.raw`: A ts object (may be mts). The right side of the regression.
- `start`: Optional starting date for the regression.
- `end`: Optional ending date for the regression.
- `intercept`: `TRUE` if there's an intercept in the regression, `FALSE` otherwise.

# Examples

```
tsreg(y, x)
tsreg(y, x, start=c(2014,1))
tsreg(y, x, end=c(2019,12))
tsreg(y, x, start=c(2000,6), end=c(2018,4))
fit <- tsreg(y, x, intercept=FALSE)

# Can treat the output like lm - because it is
AIC(fit)
coefficients(fit)
summary(fit)

# ts properties
fit$resids
fit$fitted
fit$start
fit$end
```
