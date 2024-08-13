# Chapter : Case Studies and Examples

Date-time manipulation is a critical aspect of data analysis across various fields, including finance, healthcare, and logistics. This chapter presents real-world examples of date-time manipulation using `lubridate` and solutions to common tasks.

## Real-World Examples of Date-Time Manipulation with lubridate

### Case Study 1: Financial Data Analysis

#### Scenario

You are analyzing stock market data and need to calculate the daily returns for a given stock. The dataset includes date-time stamps for each transaction.

#### Solution

```r
library(lubridate)

# Simulating stock price data
dates <- seq(ymd("2024-01-01"), ymd("2024-01-10"), by = "days")
prices <- c(100, 102, 105, 103, 107, 110, 108, 111, 115, 120)

# Creating a data frame
stock_data <- data.frame(dates, prices)

# Calculating daily returns
stock_data$returns <- c(NA, diff(stock_data$prices) / lag(stock_data$prices))
print(stock_data)
```

### Case Study 2: Healthcare Data Analysis

#### Scenario

You are working with patient admission records and need to calculate the length of stay (LOS) for each patient in the hospital.

#### Solution

```r
# Simulating patient admission and discharge data
admission_dates <- ymd("2024-01-01") + days(sample(1:10, 5, replace = TRUE))
discharge_dates <- admission_dates + days(sample(1:10, 5, replace = TRUE))

# Creating a data frame
patient_data <- data.frame(admission_dates, discharge_dates)

# Calculating the length of stay (LOS)
patient_data$length_of_stay <- discharge_dates - admission_dates
print(patient_data)
```

### Case Study 3: Logistics and Delivery Tracking

#### Scenario

You are managing a logistics company and need to calculate the delivery time for each package. The dataset includes dispatch and delivery timestamps.

#### Solution

```r
# Simulating dispatch and delivery times
dispatch_times <- ymd_hms("2024-08-01 08:00:00") + hours(sample(1:48, 5, replace = TRUE))
delivery_times <- dispatch_times + hours(sample(1:24, 5, replace = TRUE))

# Creating a data frame
logistics_data <- data.frame(dispatch_times, delivery_times)

# Calculating delivery time
logistics_data$delivery_time_hours <- as.numeric(difftime(delivery_times, dispatch_times, units = "hours"))
print(logistics_data)
```

## Common Date-Time Manipulation Tasks and Their Solutions

### Task 1: Rounding Date-Time to the Nearest Hour

```r
# Simulating a date-time object
datetime <- ymd_hms("2024-08-13 14:45:00")

# Rounding to the nearest hour
rounded_hour <- round_date(datetime, unit = "hour")
print(rounded_hour)
```

### Task 2: Converting Date-Time to a Different Time Zone

```r
# Simulating a date-time object in UTC
datetime_utc <- ymd_hms("2024-08-13 14:00:00", tz = "UTC")

# Converting to "America/New_York" time zone
datetime_ny <- with_tz(datetime_utc, tzone = "America/New_York")
print(datetime_ny)
```

### Task 3: Extracting Year, Month, and Day from a Date-Time Object

```r
# Simulating a date-time object
datetime <- ymd_hms("2024-08-13 14:30:00")

# Extracting year, month, and day
year_value <- year(datetime)
month_value <- month(datetime)
day_value <- day(datetime)

print(paste("Year:", year_value, "Month:", month_value, "Day:", day_value))
```

### Task 4: Handling Missing or Incomplete Dates

```r
# Handling a date with only year and month
year_month <- ym("2024-08")
print(year_month)

# Handling a date with year and quarter
year_quarter <- yq("2024 Q3")
print(year_quarter)
```

### Task 5: Creating a Sequence of Dates

```r
# Creating a sequence of dates from start to end with a daily interval
start_date <- as.Date("2024-08-01")
end_date <- as.Date("2024-08-10")

date_sequence <- seq(from = start_date, to = end_date, by = "day")
print(date_sequence)
```

---

This chapter provides practical examples of date-time manipulation using `lubridate`. From calculating daily returns and length of stay to managing logistics and handling incomplete dates, these case studies and solutions showcase how to apply `lubridate` in real-world scenarios. The examples and tasks presented are essential for anyone dealing with time-based data in R.
