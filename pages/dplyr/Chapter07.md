Row-wise Operations 
In data analysis, there are situations where you need to perform operations across rows rather than columns. The rowwise() function in dplyr is designed for such cases, allowing you to apply functions to each row individually. This chapter will introduce you to rowwise() and demonstrate how to apply functions across rows in a data frame.

Introduction to rowwise()
The rowwise() function is used to group a data frame by individual rows, enabling operations to be performed on a row-by-row basis. This is particularly useful when you need to apply functions that operate on multiple columns of the same row, such as calculating the sum, mean, or any custom operation across columns for each row.

Applying Functions Across Rows
Let's start by creating a sample data frame and using rowwise() to apply functions across rows.

Example:

r
Copy code
# Load the dplyr package
library(dplyr)

# Create a sample data frame
df <- data.frame(
  student = c("Alice", "Bob", "Charlie", "David"),
  math = c(85, 90, 78, 88),
  science = c(92, 85, 80, 90),
  english = c(88, 94, 82, 86)
)

# View the data frame
print(df)
This data frame contains scores for students across three subjects: math, science, and English.

Example 1: Row-wise Sum
Suppose you want to calculate the total score for each student by summing their scores across the three subjects.

r
Copy code
# Calculate the total score for each student using rowwise() and sum()
df_total <- df %>%
  rowwise() %>%
  mutate(total_score = sum(c_across(math:english)))

# View the data frame with the total_score column
print(df_total)
In this example, rowwise() is used to ensure that the sum() function is applied across each row. The c_across() function is used to select the columns across which the sum should be calculated. The result is a new total_score column that contains the sum of math, science, and English scores for each student.

Example 2: Row-wise Mean
Similarly, you might want to calculate the average score for each student across the three subjects.

r
Copy code
# Calculate the average score for each student using rowwise() and mean()
df_average <- df %>%
  rowwise() %>%
  mutate(average_score = mean(c_across(math:english)))

# View the data frame with the average_score column
print(df_average)
This code calculates the row-wise mean of the selected columns, adding a new average_score column to the data frame.

Example 3: Applying a Custom Function Across Rows
You can also apply custom functions to each row. For instance, let's calculate the range (difference between maximum and minimum scores) for each student.

r
Copy code
# Calculate the range of scores for each student using rowwise() and a custom function
df_range <- df %>%
  rowwise() %>%
  mutate(score_range = max(c_across(math:english)) - min(c_across(math:english)))

# View the data frame with the score_range column
print(df_range)
In this example, a custom function is used to calculate the range of scores across the three subjects for each student.

Example 4: Combining Multiple Row-wise Operations
You can combine multiple row-wise operations to perform more complex calculations. For example, let's calculate the total, average, and range of scores for each student.

r
Copy code
# Calculate total, average, and range of scores for each student
df_combined <- df %>%
  rowwise() %>%
  mutate(
    total_score = sum(c_across(math:english)),
    average_score = mean(c_across(math:english)),
    score_range = max(c_across(math:english)) - min(c_across(math:english))
  )

# View the data frame with all the calculated columns
print(df_combined)
This code calculates the total, average, and range of scores for each student and adds these as new columns in the data frame.

This chapter introduces rowwise() in dplyr and demonstrates how to perform row-wise operations by applying functions across rows. Whether you need to sum, average, or apply custom calculations across multiple columns for each row, rowwise() is a powerful tool that simplifies these operations, making your data analysis more efficient and flexible.
