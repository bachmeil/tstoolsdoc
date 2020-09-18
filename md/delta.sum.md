# delta.sum and se.sum

Returns the standard error, calculated by the delta method, of the sum 
of the elements of `theta`. This is a convenience function that calls
into the `deltamethod` function in the `msm` package to do the actual calculation.

# Arguments

`delta.sum <- function(theta, v)`  
`se.sum <- function(fit, m=NULL)`

- `theta`: Vector of coefficients.
- `v`: Covariance matrix corresponding to the elements of `theta`.
- `fit`: `lm` output.
- `m`: Vector holding the indexes of the coefficients to sum. If `NULL`,
it identifies all coefficients.

# Examples

`fit` is the output of a regression with three coefficients. You need
the standard error of the sum of all three coefficients.

```
delta.sum(coefficients(fit), vcov(fit))
```

`fit2` is the output of a regression with five coefficients. You need
the standard error of the sum of the second and fourth coefficients.

```
# Grab the relevant coefficients
b <- coefficients(fit)[c(2,4)]

# This will grab the right submatrix
# Keeps the elements in the right place
v <- vcov(fit)[c(2,4), c(2,4)]
delta.sum(b, v)
```

The second example is pretty verbose. You have to call the `coefficients`
function and pull out the elements you want. You have to pull the appropriate
elements out of `vcov`, and you might not even be aware of how to do it.
Therefore a further convenience function `se.sum` is included for cases
where you're working with linear regression output. Note that `delta.sum`
works with any estimation output, as long as you have the covariance
matrix.

This achieves the same thing as the previous example:

```
se.sum(fit, c(2,4))
```

If you want the standard error of the sum of all coefficients in the 
regression, you can omit the second argument:

```
se.sum(fit)
```

Please keep in mind that, while this is the most convenient case, it
only works with `lm` output.
