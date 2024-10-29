# predict.tsreg

`predict.tsreg <- function(obj, newdata=NULL)`

For making a prediction with a model estimated by `tsreg`.

- If it's called with only one argument, `predict(fit)`, where `fit` is
the output of a call to `tsreg`, it will use the last observation in the
dataset used for estimation to make the forecast. This is useful if you're
making a forecast using the h-step ahead projection approach (also called
direct estimation).
- To supply the observations to use to calculate the prediction as argument `newdata`, it needs
to be one of the following types:
  - vector: When sending a vector (which includes a ts object), it's assumed
  you're making a single prediction, so the length of the vector needs to
  be the same as the number of regressors, excluding the intercept even
  if it's included in your model. If you have four regressors plus an
  intercept, you send a vector or ts with four elements.
  - matrix or mts: Each row is treated as one observation. The number of
  columns has to be equal to the number of regresssors.
  - data frame: Variables are assumed to be in the correct order. There
  is no matching of names of variables.
  - list: You need the length of all elements to be the same. The number
  of elements has to equal the number of regressors. Variables are assumed
  to be in the correct order, so that the first coefficient goes with the
  first element, the second coefficients goes with the second elment, etc.
  Names of elements are ignored.+

# Testing Code

```
set.seed(100)
y <- ts(rnorm(100))
x <- ts(rnorm(100))
z <- ts(rnorm(100))
library(tstools)
fit <- tsreg(y, x %~% z)
print(fit)
print(predict(fit))
print(predict(fit, c(2, 3)))
print(sum(fit$coef * c(1, 2, 3)))
print(predict(fit, matrix(c(2, 3, 4, 5), ncol=2)))
print(cbind(1, matrix(c(2, 3, 4, 5), ncol=2)) %*% matrix(fit$coef, ncol=1))
print(predict(fit, data.frame(c(2, 3), c(4, 5))))
print(predict(fit, list(c(2, 3), c(4, 5))))
```
