---
id: ZGnlm1fl27ql2k7Ib3M0i
title: reverseIndex
desc: ''
updated: 1632188306837
created: 1632187754956
---

```
reverseIndex <- function(x, ii)
```

- `x`: A vector
- `ii`: Index (scalar or vector)

This returns element `ii` if `x` is reversed. `reverseIndex(x, 1)` is the last element of `x`, `reverseIndex(x, 2)` is the second to the last, and `reverseIndex(x, 1:2)` is the last two elements. Note that the elements are reversed, so that the last element is first and the second to last element is second, even though the second to last element precedes the last element.

You can achieve the same thing as `reverseIndex(x, 1:2)` by using `rev(x)[1:2]` or `x[(length(x)-1):(length(x)-2)]`. `reverseIndex` was introduced to enable cleaner code.