# Chapter : Nesting and Unnesting

Nesting and unnesting data frames are powerful techniques in R that allow you to manage complex data structures. Nesting involves creating a data frame where some columns contain entire data frames as their entries. This is particularly useful when you want to group data and then perform operations on each group individually. Unnesting is the process of expanding these nested data frames back into their original, non-nested form.

## Using `nest()` to Create Nested Data Frames

The `nest()` function is used to create nested data frames, where each row in the resulting data frame contains a list-column. Each element in this list-column is a data frame corresponding to a subset of the original data, often grouped by some key variable.

**Example:**

Let's start by creating a sample data frame that records sales data for different products across multiple stores.

```r
# Load the dplyr and tidyr packages
library(dplyr)
library(tidyr)

# Create a sample data frame
df <- data.frame(
  store = c("Store A", "Store A", "Store B", "Store B", "Store C", "Store C"),
  product = c("Apples", "Bananas", "Apples", "Bananas", "Apples", "Bananas"),
  sales = c(30, 45, 25, 35, 40, 50)
)

# View the data frame
print(df)
```

Suppose you want to group this data by store, creating a nested data frame where each store contains its own data frame of products and sales.

```r
# Nest the data frame by 'store'
df_nested <- df %>%
  group_by(store) %>%
  nest()

# View the nested data frame
print(df_nested)
```

In this example, `df_nested` is a data frame where each row corresponds to a different store, and the `data` column contains a nested data frame of the products and sales for that store.

### Example: Performing Operations on Nested Data

Once you have a nested data frame, you can apply operations to each nested data frame individually. For instance, let's calculate the total sales for each store.

```r
# Calculate total sales for each store using map() from the purrr package
df_totals <- df_nested %>%
  mutate(total_sales = map(data, ~ sum(.x$sales)))

# View the data frame with total sales
print(df_totals)
```

This code calculates the total sales for each store by applying a function to each nested data frame using the `map()` function from the `purrr` package.

## Unnesting Data Frames with `unnest()`

The `unnest()` function is used to expand a nested data frame back into its original, non-nested form. This is useful when you need to return to a flat data structure after performing operations on the nested data.

**Example:**

Let's unnest the `df_totals` data frame back to its original form.

```r
# Unnest the data frame
df_unnested <- df_totals %>%
  unnest(cols = c(data))

# View the unnested data frame
print(df_unnested)
```

This code flattens the `df_totals` data frame, returning it to a form similar to the original data frame but with the added `total_sales` column.

### Example: Selective Unnesting

You can also selectively unnest specific columns, keeping some columns nested if desired.

```r
# Selectively unnest only the 'data' column
df_selective_unnest <- df_totals %>%
  unnest(cols = c(data))

# View the selectively unnested data frame
print(df_selective_unnest)
```

In this example, the `data` column is unnested, while any other list-columns (if they existed) would remain nested.

---

This chapter introduces the concepts of nesting and unnesting in `dplyr` and `tidyr`. By nesting data frames, you can manage complex, grouped data more effectively, and by unnesting, you can return to a flat data structure for further analysis. These techniques are particularly useful in scenarios where you need to perform operations on subsets of your data before combining the results.
