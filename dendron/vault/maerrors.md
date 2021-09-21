---
id: ClEoPkeU1SlSqc7ob3VWp
title: maErrors
desc: ''
updated: 1632187713636
created: 1632187511934
---

```
maErrors <- function(y, x, f, ma.order, par)
```

- `y`: The left hand variable.
- `x`: The regressors. For an AR model, will be lags of `y`. Should not include an intercept (the intercept, if present, is handled by the user-supplied function `f`).
- `f`: Function to calculate $\varepsilon_{t}$ given $y_{t}$, $x_{t}$, and all prior values of $\varepsilon$.
- `ma.order`: Number of lagged MA terms to include.
- `par`: Vector of all coefficients.