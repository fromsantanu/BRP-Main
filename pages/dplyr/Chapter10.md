Programming with dplyr 
dplyr is not only useful for interactive data manipulation but also for programming in R. When writing functions that use dplyr, it's important to understand the concepts of non-standard evaluation (NSE) and standard evaluation (SE), as well as how to use quasiquotation with the rlang package. This chapter will cover these topics and provide examples to help you write robust and flexible data manipulation functions.

Using dplyr within Functions
When using dplyr functions inside custom R functions, you often want to pass column names as arguments. However, because dplyr uses non-standard evaluation (NSE), directly passing column names as strings or symbols requires special handling.

Example:

Suppose you want to create a function that filters rows based on a specific column and value.

r
Copy code
# Load the necessary packages
library(dplyr)

# Create a sample data frame
df <- data.frame(
  name = c("Alice", "Bob", "Charlie", "David", "Eva"),
  age = c(24, 27, 22, 32, 29),
  score = c(85, 90, 88, 92, 95)
)

# Define a function that filters rows based on a column and value
filter_by_value <- function(data, column, value) {
  data %>%
    filter({{ column }} == value)
}

# Use the function to filter by age
filtered_df <- filter_by_value(df, age, 27)

# View the filtered data frame
print(filtered_df)
In this example, the filter_by_value() function uses {{ column }} to allow non-standard evaluation (NSE) within the function, enabling the flexible passing of column names.

Non-standard Evaluation (NSE) and Standard Evaluation (SE)
dplyr uses non-standard evaluation (NSE) by default, allowing you to refer to columns directly by their names without quotation marks. However, there are situations where you might need to switch to standard evaluation (SE), such as when column names are stored as strings or variables.

Example of NSE:

r
Copy code
# Filter rows where age is greater than 25 using NSE
filtered_df_nse <- df %>%
  filter(age > 25)

# View the filtered data frame
print(filtered_df_nse)
Example of SE with filter() and sym():

r
Copy code
# Store column name as a string
column_name <- "age"

# Convert the string to a symbol and use SE
filtered_df_se <- df %>%
  filter(!!sym(column_name) > 25)

# View the filtered data frame
print(filtered_df_se)
In this example, sym() converts the string "age" into a symbol that can be evaluated within filter() using !!, a technique called "unquoting."

Quasiquotation with rlang
Quasiquotation is a powerful tool that allows you to programmatically construct and evaluate expressions in dplyr. The rlang package provides functions like !! (unquote) and !!! (unquote-splice) to support quasiquotation.

Example:

Let's create a function that allows dynamic column selection and filtering based on user input.

r
Copy code
# Load the rlang package
library(rlang)

# Define a function that dynamically selects and filters columns
dynamic_filter <- function(data, column, threshold) {
  data %>%
    filter(!!sym(column) > threshold) %>%
    select(!!sym(column))
}

# Use the function to filter and select based on 'score'
filtered_df_dynamic <- dynamic_filter(df, "score", 90)

# View the filtered and selected data frame
print(filtered_df_dynamic)
In this example, sym() is used to convert the column name string into a symbol, and !! is used to unquote the symbol within the filter() and select() functions.

Advanced Quasiquotation with !!!
You can use !!! to unquote-splice a list of arguments into a function call. This is useful when you need to pass multiple arguments dynamically.

Example:

Suppose you want to create a function that filters rows based on multiple conditions.

r
Copy code
# Define a function that filters rows based on multiple conditions
filter_multiple_conditions <- function(data, conditions) {
  data %>%
    filter(!!!conditions)
}

# Create a list of conditions
conditions <- list(quo(age > 25), quo(score > 90))

# Use the function to filter the data frame
filtered_df_multiple <- filter_multiple_conditions(df, conditions)

# View the filtered data frame
print(filtered_df_multiple)
In this example, quo() is used to quote each condition, and !!! is used to unquote-splice the list of conditions into filter().

This chapter introduces key concepts for programming with dplyr, including how to use dplyr within functions, understanding non-standard evaluation (NSE) and standard evaluation (SE), and using quasiquotation with rlang. These techniques allow you to write flexible and powerful data manipulation functions in R, making your code more adaptable and reusable.


