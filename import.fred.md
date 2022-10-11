# import.fred

`import.fred <- function(name)`

This function loads the CSV format file `name` from the local computer. The format is assumed to be the standard download format of FRED, with the date in the first column, the data in the second column, and a header in the first row. This function will NOT work if the CSV file is in any other format.

It determines the frequency of the data (monthly, quarterly, or annual), along with the first date, loads it, and returns at time series variable with the right frequency, start, and end date.

Example:

```
u <- import.fred("unrate.csv")
```

This will load the data from `unrate.csv` and create a variable `u` that holds the data with the correct time series properties.