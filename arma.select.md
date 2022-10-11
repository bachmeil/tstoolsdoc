# arma.select

`arma.select <- function(x, ar=integer(0), ma=integer(0), crit=AIC, combine=TRUE)`

Test code:

```
set.seed(100)
y <- ts(rnorm(120))
s <- arma.select(y, ar=1:4, ma=1:4)
s
s$crit
s <- arma.select(y, ar=1:4)
s
s$crit
s <- arma.select(y, ma=1:4)
s
s$crit
s <- arma.select(y, ar=1:4, ma=1:4, crit=BIC)
s
s$crit
s <- arma.select(y, ar=1:4, ma=1:4, combine=FALSE)
s
s$crit
s <- arma.select(y, ar=1:4, ma=1:4, crit=BIC, combine=FALSE)
s
s$crit
```