# Chapter : Manipulating Date-Time Objects

Manipulating date-time objects is a common task in data analysis, especially when working with time series data. The `lubridate` package provides tools to add or subtract time, round or floor dates, and adjust specific components of date-time objects.

## Adding and Subtracting Time: `+`, `-`

### Adding Time

You can easily add time intervals to date-time objects using the `+` operator along with functions like `days()`, `months()`, `years()`, etc.

```r
# Creating a date-time object
datetime <- ymd_hms("2024-08-13 14:30:00")

# Adding 5 days to the date-time object
datetime_plus_days <- datetime + days(5)
print(datetime_plus_days)

# Adding 2 months to the date-time object
datetime_plus_months <- datetime + months(2)
print(datetime_plus_months)

# Adding 1 year to the date-time object
datetime_plus_years <- datetime + years(1)
print(datetime_plus_years)
```

### Subtracting Time

Similarly, you can subtract time intervals using the `-` operator.

```r
# Subtracting 10 hours from the date-time object
datetime_minus_hours <- datetime - hours(10)
print(datetime_minus_hours)

# Subtracting 3 weeks from the date-time object
datetime_minus_weeks <- datetime - weeks(3)
print(datetime_minus_weeks)
```

## Rounding and Flooring Date-Time Objects: `floor_date()`, `ceiling_date()`, `round_date()`

### Rounding Date-Time: `round_date()`

The `round_date()` function rounds a date-time object to the nearest specified unit (e.g., nearest hour, day, month).

```r
# Rounding to the nearest hour
rounded_hour <- round_date(datetime, unit = "hour")
print(rounded_hour)

# Rounding to the nearest day
rounded_day <- round_date(datetime, unit = "day")
print(rounded_day)
```

### Flooring Date-Time: `floor_date()`

The `floor_date()` function floors a date-time object to the beginning of the specified unit.

```r
# Flooring to the beginning of the month
floored_month <- floor_date(datetime, unit = "month")
print(floored_month)

# Flooring to the beginning of the day
floored_day <- floor_date(datetime, unit = "day")
print(floored_day)
```

### Ceiling Date-Time: `ceiling_date()`

The `ceiling_date()` function adjusts a date-time object to the end of the specified unit.

```r
# Ceiling to the end of the week
ceiling_week <- ceiling_date(datetime, unit = "week")
print(ceiling_week)

# Ceiling to the end of the hour
ceiling_hour <- ceiling_date(datetime, unit = "hour")
print(ceiling_hour)
```

## Adjusting Components of Date-Time Objects: `update()`

The `update()` function allows you to adjust specific components of a date-time object, such as year, month, day, hour, minute, or second, without altering the other components.

```r
# Adjusting the year component
updated_year <- update(datetime, year = 2025)
print(updated_year)

# Adjusting the month and day components
updated_month_day <- update(datetime, month = 12, day = 25)
print(updated_month_day)

# Adjusting the time components
updated_time <- update(datetime, hour = 9, minute = 0, second = 0)
print(updated_time)
```

---

This chapter covers essential techniques for manipulating date-time objects using `lubridate`. You learned how to add and subtract time, round, floor, and ceiling date-time objects, and adjust specific components using the `update()` function. These tools provide flexibility in managing and analyzing time-based data in R.
