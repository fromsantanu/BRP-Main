# Chapter : Extracting Components of Date-Time Objects

`lubridate` makes it easy to extract various components from date-time objects, such as the year, month, day, hour, minute, second, week, weekday, and quarter. These functions are useful for breaking down and analyzing time-related data.

## Extracting Year, Month, Day, Hour, Minute, and Second

### Extracting Year: `year()`

The `year()` function extracts the year component from a date-time object.

```r
# Creating a date-time object
datetime <- ymd_hms("2024-08-13 14:30:00")

# Extracting the year
year_value <- year(datetime)
print(paste("Year:", year_value))
```

### Extracting Month: `month()`

The `month()` function extracts the month component. It can also return the month name if specified.

```r
# Extracting the month (numeric)
month_value <- month(datetime)
print(paste("Month (numeric):", month_value))

# Extracting the month (name)
month_name <- month(datetime, label = TRUE)
print(paste("Month (name):", month_name))
```

### Extracting Day: `day()`

The `day()` function extracts the day of the month.

```r
# Extracting the day
day_value <- day(datetime)
print(paste("Day:", day_value))
```

### Extracting Hour: `hour()`

The `hour()` function extracts the hour component.

```r
# Extracting the hour
hour_value <- hour(datetime)
print(paste("Hour:", hour_value))
```

### Extracting Minute: `minute()`

The `minute()` function extracts the minute component.

```r
# Extracting the minute
minute_value <- minute(datetime)
print(paste("Minute:", minute_value))
```

### Extracting Second: `second()`

The `second()` function extracts the second component.

```r
# Extracting the second
second_value <- second(datetime)
print(paste("Second:", second_value))
```

## Extracting Week and Weekday

### Extracting Week: `week()`

The `week()` function extracts the week number of the year from a date-time object.

```r
# Extracting the week of the year
week_value <- week(datetime)
print(paste("Week of the year:", week_value))
```

### Extracting Weekday: `wday()`

The `wday()` function extracts the day of the week. It can return the day number (1 = Sunday, 7 = Saturday) or the day name if specified.

```r
# Extracting the weekday (numeric)
weekday_value <- wday(datetime)
print(paste("Weekday (numeric):", weekday_value))

# Extracting the weekday (name)
weekday_name <- wday(datetime, label = TRUE)
print(paste("Weekday (name):", weekday_name))
```

## Extracting Quarter: `quarter()`

The `quarter()` function extracts the quarter of the year from a date-time object.

```r
# Extracting the quarter of the year
quarter_value <- quarter(datetime)
print(paste("Quarter of the year:", quarter_value))
```

You can also extract the quarter along with the year in a formatted string.

```r
# Extracting the quarter with year
quarter_year <- quarter(datetime, with_year = TRUE)
print(paste("Quarter with year:", quarter_year))
```

---

This chapter guides you through extracting various components from date-time objects using `lubridate`. You learned how to extract the year, month, day, hour, minute, second, week, weekday, and quarter. These functions provide a powerful way to break down and analyze date-time data for your analysis and reporting needs.
