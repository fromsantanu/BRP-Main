# Chapter : Window Functions 

Window functions are a powerful set of tools in `dplyr` that allow you to perform calculations across sets of data, maintaining the original size of the data frame. Unlike summary functions that reduce the number of rows, window functions return a vector of the same length as the input. This chapter will cover the basics of window functions, including the use of `lead()`, `lag()`, and various cumulative functions like `cummean()`, `cumsum()`, `cummin()`, and `cummax()`.

## Introduction to Window Functions

Window functions operate over a "window" or subset of your data, defined by rows relative to the current row. These functions are particularly useful when you need to calculate running totals, moving averages, or when you need to reference previous or next values in your dataset.

## Using `lead()` and `lag()`

The `lead()` and `lag()` functions are used to access subsequent or previous values in a vector, respectively. They are often used to calculate changes over time or differences between consecutive observations.

**Example:**

```r
# Load the dplyr package
library(dplyr)

# Create a sample data frame
df <- data.frame(
  day = 1:5,
  sales = c(200, 210, 190, 215, 220)
)

# Use lead() to get the next day's sales
df_lead <- df %>% mutate(next_day_sales = lead(sales))

# Use lag() to get the previous day's sales
df_lag <- df %>% mutate(previous_day_sales = lag(sales))

# View the data frames with lead and lag columns
print(df_lead)
print(df_lag)
```

In this example, `lead()` creates a new column `next_day_sales` that shifts the `sales` column forward, while `lag()` creates a `previous_day_sales` column that shifts the `sales` column backward.

## Cumulative Functions: `cummean()`, `cumsum()`, `cummin()`, `cummax()`

Cumulative functions calculate running totals, averages, or minimum/maximum values across a dataset. These functions are useful for analyzing trends over time.

**Example:**

1. **Cumulative Sum (`cumsum()`)**

   ```r
   # Calculate the cumulative sum of sales
   df_cumsum <- df %>% mutate(cumulative_sales = cumsum(sales))

   # View the data frame with the cumulative sum column
   print(df_cumsum)
   ```

   This code adds a `cumulative_sales` column that represents the running total of sales.

2. **Cumulative Mean (`cummean()`)**

   ```r
   # Calculate the cumulative mean of sales
   df_cummean <- df %>% mutate(cumulative_mean_sales = cummean(sales))

   # View the data frame with the cumulative mean column
   print(df_cummean)
   ```

   This code adds a `cumulative_mean_sales` column that represents the running average of sales.

3. **Cumulative Minimum (`cummin()`)**

   ```r
   # Calculate the cumulative minimum of sales
   df_cummin <- df %>% mutate(cumulative_min_sales = cummin(sales))

   # View the data frame with the cumulative minimum column
   print(df_cummin)
   ```

   This code adds a `cumulative_min_sales` column that represents the minimum sales observed up to each point in time.

4. **Cumulative Maximum (`cummax()`)**

   ```r
   # Calculate the cumulative maximum of sales
   df_cummax <- df %>% mutate(cumulative_max_sales = cummax(sales))

   # View the data frame with the cumulative maximum column
   print(df_cummax)
   ```

   This code adds a `cumulative_max_sales` column that represents the maximum sales observed up to each point in time.

## Combining Window Functions

You can combine multiple window functions to perform complex analyses. For example, you might calculate both the cumulative sum and the difference between consecutive days' sales.

**Example:**

```r
# Combine lag() and cumsum()
df_combined <- df %>% 
  mutate(
    previous_day_sales = lag(sales),
    sales_difference = sales - lag(sales),
    cumulative_sales = cumsum(sales)
  )

# View the data frame with combined window functions
print(df_combined)
```

This code creates columns for the previous day's sales, the difference in sales between consecutive days, and the cumulative sum of sales.

---

This chapter introduces window functions in `dplyr` and demonstrates how to use `lead()`, `lag()`, and various cumulative functions like `cummean()`, `cumsum()`, `cummin()`, and `cummax()` for advanced data manipulation. These functions are essential tools for performing running calculations, trend analysis, and other tasks that require referencing other rows in a dataset.
