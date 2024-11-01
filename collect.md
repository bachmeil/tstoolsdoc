# collect

## Overview

This function pulls elements from a list, optionally transforming them in some way, and then converting the output to the desired data structure.

`collect.list <- function(x, name=NULL, transform=NULL, output="list")`

- `x`: The list to pull elements from.
- `name`: The name of the variable to pull from each element of the list. If `NULL`, will pull the whole list element.
- `what`: "rows" to convert each element to a row of a matrix, "cols" to convert each element to a column of a matrix, "numeric" to convert each element to a numeric vector element, "character" to convert each element to a string in a vector, "logical" to convert to `TRUE` or `FALSE` in a vector, and "list" to convert all the elements pulled into a list.
- `transform`: Optional function you can send to operate on each of the elements you pull out before storing them.

## Motivation

The list is an important data structure in R. Representing heterogenous data is important for such things as regression output and simulation results.

Unfortunately, it can be a nightmare to extract the information you want from a list. This has caused much pain for new users of the language, particularly students using R for a class.

The `collect` function does three things:

- Converting lists into other data structures, such as vectors and matrices.
- Pulling out parts of each element of a list.
- Transforming the elements of a list.

I will now go into detail on each of area of functionality.

## Converting lists to other data structures

### Numeric vectors

Suppose you have just done a call to lapply, and you have a list with the following elements:

```
x <- list(1.5, 2.7, 4.2, 3.9)
```

That's a vector, so go ahead and multiply each element by 2.5:

```
2.5 * x
```

That blew up on you. You get the error message

```
Error in 2.5 * x : non-numeric argument to binary operator
```

Not exactly the most insightful error message, considering this operation should work. The problem is that R does not know the properties of the individual elements of a list. There is no way for R to know that multiplying by 2.5 is defined for every element. What if one of the elements is the string "dog"? How would you multiply a string by 2.5?

The simplest use of `collect` is to convert your list to a different data structure. In this case, we want to clarify that the elements of `x` can be treated as the elements of a numeric vector. You can do this:

```
y <- collect(x, output="numeric")
y
```

This tells R to collect each element of the list `x` and store them in a numeric vector. Of course, this will only work properly if the elements really are scalar numbers, but the whole purpose of `collect` is to give that kind of information to R.

```
2.5 * y
```

Which is exactly what you want.

### Other vector types

It works for other vector types as well, including character and logical:

```
x1 <- list("a", "b", "c")
y1 <- collect(x1, output="character")
y1

x2 <- list(TRUE, TRUE, FALSE, TRUE)
y2 <- collect(x2, output="logical")
y2
```

### Matrix

You can convert the list to a matrix if each element holds a vector. For instance, you might have a vector of estimated coefficients for many subsamples. You can treat each element as a row or column of the output matrix.

```
x <- list(c(1.1, 2.2, 3.3), c(4.4, 5.5, 6.6))
y1 <- collect(x, output="rows")
y1
y2 <- collect(x, output="cols")
y2
```

### Array

If each list element is a matrix, you can convert the list to a 3D array.

```
x <- list(matrix(1:9, ncol=3), matrix(10:18, ncol=3))
y <- collect(x, output="3d")
y
```

## Pulling out parts of each element of the list

Sometimes you want to pull out only part of the output of each element of the list. For instance, suppose you have a vector of data and its mean in each element of the list.

```
x <- list(list(data=1:3, mu=2), list(data=4:6, mu=5), list(data=7:9, mu=8))
x
```

You can grab just the means as a numeric vector:

```
collect(x, name="mu", output="numeric")
```

Note that if you omit the `output` argument, it will return a list:

```
collect(x, name="mu")
```

Although it's more bug-prone, you can also give a numerical index for `name`. In some cases, this may be the only option. You can achieve the same as the previous example by doing

```
collect(x, name=2, output="numeric")
```

This should generally be avoided whenever a character name is available, as among other things, your program will remain valid if the order of the output in the list elements changes. If the names of the output change, it will lead to an error when specifying a character name.

## Transforming the elements of a list

At a more general level, you may want to transform the elements of a list. To make this concrete, suppose you have generated three datasets, estimated a regression using each of them, and saved the results in a list. You want to pull the t-statistic on the second coefficient for each, collecting the results in a vector. For this situation, you can add a function that operates on each element of the list and returns the output you're after.

This example is more involved due to the fact that this is for more advanced use cases.

```
set.seed(451)
x1 <- rnorm(100)
y1 <- rnorm(100)
x2 <- rnorm(100)
y2 <- rnorm(100)
x3 <- rnorm(100)
y3 <- rnorm(100)

results <- list(lm(y1~x1), lm(y2~x2), lm(y3~x3))
collect(results, transform=function(el) { summary(el)$coefficients[1,3] }, output="numeric")
```

Note: If you have both `name` and `transform` as arguments, the `transform` function is applied after pulling out the desired component.