# Chapter : Creating Date-Time Objects

## Creating Date-Time Objects: ymd(), mdy(), dmy()

The `lubridate` package provides a set of functions specifically designed to create date-time objects from character strings. The functions `ymd()`, `mdy()`, and `dmy()` are used to parse dates in different formats—Year-Month-Day, Month-Day-Year, and Day-Month-Year, respectively.

### Using ymd()

The `ymd()` function is used when the date is in the format Year-Month-Day.

```r
# Creating a date-time object with ymd()
date_ymd <- ymd("2024-08-13")
print(date_ymd)

# Checking the class of the object
print(class(date_ymd))
```

### Using mdy()

The `mdy()` function is used when the date is in the format Month-Day-Year.

```r
# Creating a date-time object with mdy()
date_mdy <- mdy("08-13-2024")
print(date_mdy)

# Checking the class of the object
print(class(date_mdy))
```

### Using dmy()

The `dmy()` function is used when the date is in the format Day-Month-Year.

```r
# Creating a date-time object with dmy()
date_dmy <- dmy("13-08-2024")
print(date_dmy)

# Checking the class of the object
print(class(date_dmy))
```

## Creating Date-Time Objects with Time: ymd_hms(), mdy_hms(), dmy_hms()

When you need to include time components (hours, minutes, seconds) along with the date, `lubridate` provides functions like `ymd_hms()`, `mdy_hms()`, and `dmy_hms()`.

### Using ymd_hms()

The `ymd_hms()` function parses date-time strings that include hours, minutes, and seconds, in the format Year-Month-Day Hour:Minute:Second.

```r
# Creating a date-time object with ymd_hms()
datetime_ymd_hms <- ymd_hms("2024-08-13 14:30:00")
print(datetime_ymd_hms)

# Checking the class of the object
print(class(datetime_ymd_hms))
```

### Using mdy_hms()

The `mdy_hms()` function parses date-time strings in the format Month-Day-Year Hour:Minute:Second.

```r
# Creating a date-time object with mdy_hms()
datetime_mdy_hms <- mdy_hms("08-13-2024 14:30:00")
print(datetime_mdy_hms)

# Checking the class of the object
print(class(datetime_mdy_hms))
```

### Using dmy_hms()

The `dmy_hms()` function parses date-time strings in the format Day-Month-Year Hour:Minute:Second.

```r
# Creating a date-time object with dmy_hms()
datetime_dmy_hms <- dmy_hms("13-08-2024 14:30:00")
print(datetime_dmy_hms)

# Checking the class of the object
print(class(datetime_dmy_hms))
```

## Parsing Dates with Custom Formats: parse_date_time()

Sometimes, the date-time strings may not follow standard formats. In such cases, `parse_date_time()` allows you to specify custom formats for parsing.

### Using parse_date_time()

The `parse_date_time()` function is highly flexible and can parse dates with custom formats by specifying the order of date and time components.

```r
# Parsing a custom date-time format
custom_datetime <- parse_date_time("13/08/2024 14:30:00", orders = "dmy HMS")
print(custom_datetime)

# Checking the class of the object
print(class(custom_datetime))
```

You can also handle multiple formats in a single function call by passing a vector of formats.

```r
# Parsing multiple date-time formats
multiple_formats <- parse_date_time(c("2024-08-13 14:30:00", "08/13/2024 02:30:00 PM"),
                                    orders = c("ymd HMS", "mdy IMS p"))
print(multiple_formats)
```

---

This chapter introduces you to creating date-time objects using `lubridate`, covering basic functions like `ymd()`, `mdy()`, `dmy()` for dates, and their counterparts `ymd_hms()`, `mdy_hms()`, `dmy_hms()` for date-time objects with time. Additionally, it explores the `parse_date_time()` function for parsing dates with custom formats, offering flexibility for various scenarios.
