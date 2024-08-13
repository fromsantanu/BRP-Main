# Chapter : Dealing with Incomplete Dates

In some datasets, you may encounter incomplete date information, such as records that only provide the year and month, or the year and day. The `lubridate` package provides functions like `ym()`, `yq()`, and `yd()` to handle these incomplete dates effectively.

## Handling Incomplete Dates with `ym()`

### Using `ym()` for Year and Month

The `ym()` function is designed to handle dates where only the year and month are provided. It returns a date-time object with the day set to the first of the month by default.

```r
# Handling a year and month date string
year_month <- ym("2024-08")
print(year_month)

# Checking the class of the object
print(class(year_month))
```

### Practical Example: Aggregating Monthly Data

If you have monthly data and need to convert it into date-time objects for analysis, `ym()` is very useful.

```r
# Simulating a dataset with year and month information
monthly_data <- c("2024-01", "2024-02", "2024-03")

# Converting to date-time objects
monthly_dates <- ym(monthly_data)
print(monthly_dates)
```

## Handling Incomplete Dates with `yq()`

### Using `yq()` for Year and Quarter

The `yq()` function is used when the data contains the year and quarter information. It returns a date-time object with the day set to the first day of the first month in the quarter.

```r
# Handling a year and quarter date string
year_quarter <- yq("2024 Q1")
print(year_quarter)

# Checking the class of the object
print(class(year_quarter))
```

### Practical Example: Quarterly Reporting

For financial or business reporting on a quarterly basis, `yq()` can convert quarter information into date-time objects for further analysis.

```r
# Simulating a dataset with year and quarter information
quarterly_data <- c("2024 Q1", "2024 Q2", "2024 Q3")

# Converting to date-time objects
quarterly_dates <- yq(quarterly_data)
print(quarterly_dates)
```

## Handling Incomplete Dates with `yd()`

### Using `yd()` for Year and Day

The `yd()` function handles dates where only the year and day of the year are provided (e.g., the 100th day of the year). This function is useful for Julian dates or other systems that record the day of the year.

```r
# Handling a year and day-of-year date string
year_day <- yd("2024-150")
print(year_day)

# Checking the class of the object
print(class(year_day))
```

### Practical Example: Environmental Data Analysis

In environmental studies, data might be recorded based on the day of the year. `yd()` allows you to convert these records into full date-time objects.

```r
# Simulating a dataset with year and day-of-year information
daily_data <- c("2024-001", "2024-150", "2024-365")

# Converting to date-time objects
daily_dates <- yd(daily_data)
print(daily_dates)
```

---

This chapter covers handling incomplete dates using `lubridate` functions like `ym()`, `yq()`, and `yd()`. These functions allow you to work with partial date information, converting it into complete date-time objects for analysis. Whether dealing with monthly data, quarterly reports, or day-of-year records, these tools help manage and analyze incomplete date data effectively.
