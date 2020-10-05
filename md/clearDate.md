# clearDate

R's reporting of monthly dates as decimal values is confusing. This
function reports the month and year of the observation in a clear fashion.

The main use case for this function is to convert a month of the form
2017.5 into the readable and less bug-prone form "July 2017". Most beginners
to R time series (and many experienced users) would interpret 2017.5 as June 2017.
Even worse is ugly output like 2017.917.

There are good reasons to use decimal numbers like that for internal
date storage. That *does not* mean it's a good way to report dates to
the user.

## Normal usage

```
clearDate(2017.5)
clearDate(2017.083)
```

The output is

```
[1] "Jul 2017"
[1] "Feb 2017"
```

## Other usage

```
clearDate(c(2017,4))
```

Although `c(2017,4)` is clear, the user may want alternative output:

```
[1] "Apr 2017"
```

## Changing the output

It's occasionally useful to convert a monthly date into vector form. For
instance, 2017.5 converts to `c(2017,7)`. The main use case would be to
grab the month number from a decimal date.

Input:

```
clearDate(c(2017,4), "vector")
clearDate(c(2017,4), "vector")[2]
```

Output:

```
[1] 2017    4
[1] 4
```

Input:

```
clearDate(2017.083, "vector")
```

Output:

```
[1] 2017    2
```
