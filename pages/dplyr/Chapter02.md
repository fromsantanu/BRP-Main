# Core Verbs in dplyr

The core verbs of `dplyr` are designed to make data manipulation intuitive and efficient. These verbs allow you to perform common data wrangling tasks such as subsetting rows, selecting columns, creating new variables, reordering rows, summarizing data, and grouping data. Below are examples of how to use each of these core verbs.

### filter(): Subsetting Rows

The `filter()` function is used to subset rows based on one or more conditions. Only rows that meet the specified conditions will be retained in the output.

**Example:**

```r
# Load the dplyr package
library(dplyr)

# Create a sample data frame
df <- data.frame(
  name = c("Alice", "Bob", "Charlie", "David", "Eva"),
  age = c(24, 27, 22, 32, 29),
  score = c(85, 90, 88, 92, 95)
)

# Filter rows where age is greater than 25
df_filtered <- df %>% filter(age > 25)

# View the filtered data frame
print(df_filtered)
```

This code filters the rows to include only those where `age` is greater than 25.

### select(): Selecting Columns

The `select()` function is used to choose specific columns from a data frame. This is useful when you want to focus on a subset of variables.

**Example:**

```r
# Select the name and score columns
df_selected <- df %>% select(name, score)

# View the selected data frame
print(df_selected)
```

This code selects only the `name` and `score` columns from the data frame.

### mutate(): Adding New Variables

The `mutate()` function is used to create new variables or modify existing ones. It adds new columns to the data frame while keeping the original columns intact.

**Example:**

```r
# Add a new column grade based on score
df_mutated <- df %>% mutate(
  grade = ifelse(score >= 90, "A", "B")
)

# View the mutated data frame
print(df_mutated)
```

This code adds a new column `grade`, assigning a grade of "A" if the score is 90 or higher, and "B" otherwise.

### arrange(): Reordering Rows

The `arrange()` function is used to reorder the rows of a data frame based on the values of one or more columns. By default, it orders rows in ascending order, but you can specify descending order as well.

**Example:**

```r
# Arrange rows in descending order of score
df_arranged <- df %>% arrange(desc(score))

# View the arranged data frame
print(df_arranged)
```

This code arranges the rows of the data frame in descending order of `score`.

### summarise(): Summarizing Data

The `summarise()` function is used to calculate summary statistics for a data frame. It reduces multiple values down to a single summary, such as the mean, sum, or count.

**Example:**

```r
# Calculate the average score
df_summary <- df %>% summarise(
  average_score = mean(score)
)

# View the summary
print(df_summary)
```

This code calculates the average of the `score` column and returns a data frame with the result.

### group_by(): Grouping Data

The `group_by()` function is used to group data by one or more variables. It is often used in conjunction with `summarise()` to calculate summary statistics for each group.

**Example:**

```r
# Group by grade and calculate average age
df_grouped <- df %>% 
  mutate(grade = ifelse(score >= 90, "A", "B")) %>%
  group_by(grade) %>% 
  summarise(average_age = mean(age))

# View the grouped summary
print(df_grouped)
```

This code first creates a `grade` variable, then groups the data by `grade` and calculates the average `age` for each group.

---

This chapter demonstrates how to use the core verbs of `dplyr` to perform essential data manipulation tasks in R. These verbs form the foundation of data wrangling in `dplyr`, allowing you to filter, select, mutate, arrange, summarise, and group your data with ease.
