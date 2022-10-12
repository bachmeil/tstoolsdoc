# Date Arithmetic

Operators to simplify arithmetic with monthly or quarterly dates.

Examples:

```
# Add months to date
# c(2011,5)
c(2010,12) %m+% 5

# Subtract months from date
# c(2009,11)
c(2010,12) %m-% 13

# Add quarters to date
# c(2011,3)
c(2010,4) %q+% 3

# Subtract quarters from date
# c(2009,4)
c(2010,4) %q-% 4
```