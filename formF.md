# formF

`formF <- function(varfit, constant=TRUE)`

- `varfit` is the output of a call to `VAR` in the vars package
- `constant` is TRUE if you have a constant term in the estimated VAR model and you want to keep it. For calculation of linear IRFs, you'll normally want `constant` to be FALSE.

Example:

```
fit <- VAR(dataset)
formF(fit)
```