# armafit

The default ARMA estimation function is somewhat unfriendly. Most notably, it throws students off by calling something an "intercept" when it's actually the mean.

Example usage:

```
f <- armafit(x, 1, 1) # Estimate ARMA(1,1) model of x
f <- armafit(x, 1) # Estimate AR(1) model of x
f <- armafit(x, ma=4) # Estimate MA(4) model of x
f <- armafit(x, 3, 2)
f <- armafit(x, ar=2)
```

**Print the coefficients**

```
f$par
```

Notes:

- There's no standard error reported for the intercept.
- This really is the intercept, not the mean, as reported by `arima`.

**Make predictions**

```
predict(f, 12) # Horizon 1-12 predictions
```

**Fitted values**

```
f$fitted
```

**Residuals**

```
f$residuals
```

**Compatibility with Arima objects**

The output is fully compatible with an Arima object. You can use it as an argument with any function expecting Arima output. Examples:

```
AIC(f) # Calls the function for Arima object
BIC(f)
```