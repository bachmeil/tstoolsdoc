# `wald`

The function `wald` does a Wald test. You supply the constraints. Implementation follows Cameron and Trivedi (2005, page 136). The constraints take the form $R \widehat{\theta} - q = 0$.

## Signature

`wald <- function(R, q, theta, V)`

## Arguments

`R` and `q` describe the constraints. `theta` is the estimated coefficient vector of the unrestricted model. `V` is the variance-covariance matrix of the unrestricted model. You can either send `vcov(fit)` where `fit` is the output of a call to `lm` or a similar regression function, or send your own variance-covariance matrix, which would be the case if you correct for heteroskedasticity or serial correlation.

Normally you would use `lmtest::waldtest` if you have a single regression. This function would help if you don't want to write out a formula for your regression.

## Test Case

This is the code I used to test it:

```
y <- rnorm(100)
x <- matrix(rnorm(600), ncol=6)
x1 <- x[,1:2]
x2 <- x[,3:6]
fit1 <- lm(y~x2)
fit2 <- lm(y~x1+x2)
lmtest::waldtest(fit2, fit1, test="Chisq")

R <- matrix(0.0, ncol=7, nrow=2)
R[1,2] <- 1
R[2,3] <- 1
q <- c(0.0, 0.0)
tstools::wald(R, q, fit2$coef, vcov(fit2))
```

They return the same result. There may be edge cases that have not been tested.