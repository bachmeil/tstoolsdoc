# collect

This function pulls elements from a list.

`collect.list <- function(x, name=NULL, what="numeric", transform=NULL)`

- `x`: The list to pull elements from.
- `name`: The name of the variable to pull from each element of the list. If `NULL`, will pull the whole list element.
- `what`: "rows" to convert each element to a row of a matrix, "cols" to convert each element to a column of a matrix, "numeric" to convert each element to a numeric vector element, "character" to convert each element to a string in a vector, "logical" to convert to `TRUE` or `FALSE` in a vector, and "list" to convert all the elements pulled into a list.
- `transform`: Optional function you can send to operate on each of the elements you pull out before storing them.

R lists can be useful as a way to capture heterogenous output. Unfortunately, it can be a nightmare to pull out the information you want from a list. This function facilitates conversion of list elements into other data structures, plus various transformations. It is easiest to understand how to use the function by looking at some examples.

```
x <- list(list(a=1, b=2), list(a=4, b=6))
collect(x, name="a") # vector with elements [1 4]
collect(x, name="b") # vector with elements [2 6]
collect(x, name="a", transform=function(z) { z^2 }) # vector with elements [1 16]
collect(x, transform=function(z) { z$a * z$b }) # vector with elements [2 24]

x2 <- list(list(a=1, b=2, j=TRUE), list(a=4, b=6, j=FALSE))
collect(x2, name="j", what="logical") # vector with elements [TRUE FALSE]
```