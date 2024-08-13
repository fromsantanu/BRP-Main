
# Chapter : Introduction to dplyr

The `dplyr` package is a powerful and popular tool for data manipulation in R. It provides a suite of functions that are designed to work with data frames and make data wrangling more efficient and intuitive. `dplyr` is part of the tidyverse, a collection of R packages designed for data science.

### Overview of dplyr

`dplyr` simplifies many common data manipulation tasks, such as filtering rows, selecting columns, arranging rows, adding new columns, and summarizing data. The package is built around a core set of functions, also known as "verbs," that perform these operations. The most commonly used verbs in `dplyr` include:

- `filter()`: Subset rows based on conditions.
- `select()`: Choose specific columns.
- `mutate()`: Create new columns or modify existing ones.
- `arrange()`: Reorder rows based on column values.
- `summarise()`: Aggregate data into summary statistics.
- `group_by()`: Group data by one or more variables.

These functions work seamlessly with the `%>%` operator, also known as the pipe operator, which allows for chaining multiple operations in a readable and concise manner.

### Installation and Setup

To use `dplyr`, you first need to install it from CRAN (The Comprehensive R Archive Network). If you haven't installed it yet, you can do so by running the following command:

```r
# Install dplyr from CRAN
install.packages("dplyr")
```

Once installed, you can load the package into your R session using the `library()` function:

```r
# Load the dplyr package
library(dplyr)
```

### Basic Example

Let's start with a simple example to illustrate how `dplyr` works. Suppose we have the following data frame:

```r
# Create a sample data frame
df <- data.frame(
  name = c("Alice", "Bob", "Charlie", "David", "Eva"),
  age = c(24, 27, 22, 32, 29),
  score = c(85, 90, 88, 92, 95)
)

# View the data frame
print(df)
```

This data frame contains three columns: `name`, `age`, and `score`. We can use `dplyr` to perform various data manipulation tasks on this data frame.

1. **Filtering Rows**: Use `filter()` to select rows based on conditions. For example, let's filter the data to show only the rows where `age` is greater than 25.

    ```r
    # Filter rows where age is greater than 25
    df_filtered <- df %>% filter(age > 25)

    # View the filtered data frame
    print(df_filtered)
    ```

2. **Selecting Columns**: Use `select()` to choose specific columns. For example, let's select only the `name` and `score` columns.

    ```r
    # Select the name and score columns
    df_selected <- df %>% select(name, score)

    # View the selected data frame
    print(df_selected)
    ```

3. **Arranging Rows**: Use `arrange()` to reorder rows based on column values. For example, let's arrange the data in descending order of `score`.

    ```r
    # Arrange rows in descending order of score
    df_arranged <- df %>% arrange(desc(score))

    # View the arranged data frame
    print(df_arranged)
    ```

4. **Mutating Columns**: Use `mutate()` to add new columns or modify existing ones. For example, let's create a new column `grade` based on the `score`.

    ```r
    # Add a new column grade based on score
    df_mutated <- df %>% mutate(
      grade = ifelse(score >= 90, "A", "B")
    )

    # View the mutated data frame
    print(df_mutated)
    ```

5. **Summarizing Data**: Use `summarise()` to compute summary statistics. For example, let's calculate the average `score`.

    ```r
    # Calculate the average score
    df_summary <- df %>% summarise(
      average_score = mean(score)
    )

    # View the summary
    print(df_summary)
    ```

6. **Grouping Data**: Use `group_by()` in combination with `summarise()` to calculate summary statistics by group. For example, let's group the data by `grade` and calculate the average `age` for each group.

    ```r
    # Group by grade and calculate average age
    df_grouped <- df %>% 
      mutate(grade = ifelse(score >= 90, "A", "B")) %>%
      group_by(grade) %>% 
      summarise(average_age = mean(age))

    # View the grouped summary
    print(df_grouped)
    ```

---

This chapter provides a basic introduction to the `dplyr` package, covering its core functionality and demonstrating how to perform common data manipulation tasks. As you become more familiar with `dplyr`, you'll find that it greatly simplifies your data wrangling workflow in R.
